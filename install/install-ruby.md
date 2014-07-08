### install ruby

    sudo apt-get update
    sudo apt-get install git-core
    git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc
    source ~/.bashrc
    type rbenv => rbenv is a function
    git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    git clone https://github.com/sstephenson/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash
    sudo apt-get install build-essential libssl-dev libcurl4-openssl-dev libreadline-dev -y
    rbenv install --list
    rbenv install 2.1.2
    rbenv global 2.1.2
    ruby -v
    echo "gem: --no-ri --no-rdoc" >> ~/.gemrc
    sudo ln -s /usr/bin/gcc /usr/bin/gcc-4.2
    gem install bundler
    
### install gems

    bundle install --without development test mysql aws
    ...or
    bundle install --with deployment --without development test mysql aws
