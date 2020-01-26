FROM ubuntu:18.04

RUN apt-get update \
    && apt-get install -y curl git htop vim build-essential libssl-dev zlib1g-dev libpq-dev

ENV PATH /root/.rbenv/shims:/root/.rbenv/plugins/ruby-build/bin:/root/.rbenv/bin:$PATH

RUN git clone https://github.com/rbenv/rbenv.git /root/.rbenv \
    && git clone https://github.com/rbenv/ruby-build.git /root/.rbenv/plugins/ruby-build \
    && echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc \
    && echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc \
    && echo 'eval "$(rbenv init -)"' >> ~/.bashrc

RUN echo $PATH && eval "$(rbenv init -)" \
    && rbenv install 2.7.0 \
    && rbenv global 2.7.0 \
    && echo 'export PATH="$HOME/.rbenv/shims/:$PATH"' >> ~/.bashrc

RUN gem install bundler

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - \
    && apt-get install -y nodejs

RUN gem install rails -v 6.0.2.1 \
    && rbenv rehash

WORKDIR /var/www/app







