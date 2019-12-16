这是运行的 Rails 的基本 Docker 镜像
Docker Image tag: wppurking/ruby
检查: ruby -r rbconfig -e "puts RbConfig::CONFIG['LIBS']"

- apt for
    - pg, mysql, sqlite3
    - xml
    - imagemagick
    - git, vim, curl
- ruby 2.6.5
    - jemalloc
    - gem 3.1.1
    - bundler 2.1.0
- node 8.11.2
    - npm
    - yarn

