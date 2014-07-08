https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/install/installation.md

#### symlink gcc

    sudo ln -s /usr/bin/gcc /usr/bin/gcc-4.2

#### bcrypt-ruby

install bcrypt-ruby in global gemset

    gem install bcrypt-ruby -v '3.1.2'

...installs ok

#### use global gemset
    
disable bundle install location in .bundle/config so as to use global gemset

#### nokogiri

install nokogiri globally

    gem install nokogiri -v '1.6.1'

...installs ok

#### rubyracer

install libv8

    sudo apt-get install libv8-dev

...required

install libv8 gem in global gemset

    gem install libv8
    
...installs ok (Successfully installed libv8-3.16.14.3)

install rubyracer globally

    gem install therubyracer -v '0.12.0'

breaks with "relocation R_ARM_THM_MOVW_ABS_NC against `a local symbol' can not be used when making a shared object; recompile with -fPIC", so try

    gem install therubyracer -v '0.12.0' -- -fPIC
    
breaks
    
    gem install therubyracer -v '0.12.1' -- -fPIC
    Fetching: ref-1.0.5.gem (100%)
    Successfully installed ref-1.0.5
    Fetching: libv8-3.16.14.3.gem (100%)
    Building native extensions with: '-fPIC'
    This could take a while...

also breaks

    linking shared-object v8/init.so
    /usr/bin/ld: /home/git/.rbenv/versions/2.1.2/lib/ruby/gems/2.1.0/gems/libv8-3.16.14.3/vendor/v8/out/arm.release/obj.target/tools/gyp/libv8_base.a(api.o): relocation R_ARM_THM_MOVW_ABS_NC against `a local symbol' can not be used when making a shared object; recompile with -fPIC
    /home/git/.rbenv/versions/2.1.2/lib/ruby/gems/2.1.0/gems/libv8-3.16.14.3/vendor/v8/out/arm.release/obj.target/tools/gyp/libv8_base.a: could not read symbols: Bad value
    collect2: ld returned 1 exit status
    make: *** [init.so] Error 1
    make failed, exit code 2
    Gem files will remain installed in /home/git/.rbenv/versions/2.1.2/gemsets/global/gems/therubyracer-0.12.1 for inspection.
    Results logged to /home/git/.rbenv/versions/2.1.2/gemsets/global/extensions/armv7l-linux/2.1.0-static/therubyracer-0.12.1/gem_make.out

try building libv8 with system-v8

    gem install libv8 -v 3.16.14.3 -- --with-system-v8

and then install rubyracer but still breaks.

#### execjs

could the problem be resolved by switching to execjs?

https://github.com/sstephenson/execjs

#### possible fix

https://github.com/cowboyd/therubyracer/issues/186
https://github.com/cowboyd/libv8/tree/3.11#bring-your-own-v8

still no solution

#### possible working solution

remove rubyracer from gemfile

    bundle install

edit .bundle/config

    BUNDLE_WITHOUT: development:test:mysql:aws
    BUNDLE_FROZEN: '1'
    # BUNDLE_PATH: vendor/bundle
    BUNDLE_DISABLE_SHARED_GEMS: '1'

install gems

    bundle install

done
