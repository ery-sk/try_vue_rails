# Railsアプリケーションに後から部分的にVueを導入する

```sh
ruby -v
# ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-darwin17]

rails -v
# Rails 5.2.3

bundler -v
# Bundler version 1.17.2

node -v
# v12.4.0

yarn -v
# 1.16.0
```

## 普通にアプリケーションを作成する

```sh
rails new . -T -O
rails g controller hello index
```
```rb
# config/routes.rb
Rails.application.routes.draw do
  root 'hello#index'
end
```
```sh
# 確認
bin/rails s
```

## 適当なjQueryを使う
```sh
echo "gem 'jquery-rails'" >> Gemfile
bundle
```
```js
//= require jquery
```
```html
<%= button_tag 'Hello', type: 'button', id: 'hello-jquery' %>
```
```coffee
$ ->
  $('#hello-jquery').click ->
    alert('Hello jQuery')
```
```sh
# 確認
bin/rails s
```
## WebpackerとVueの導入
```sh
echo "gem 'webpacker'" >> Gemfile
bundle
rails webpacker:install
rails webpacker:install:vue
```
```sh
ls bin/
# bundle			setup			webpack
# rails			spring			webpack-dev-server
# rake			update			yarn
```

## jQueryとVueの共存確認

```html
<!-- app/views/hello/index.html.erb -->
<%= javascript_pack_tag 'hello_vue' %>
```

起動

```sh
$ bin/webpack-dev-server
$ bin/rails s
```
<img width="1279" alt="vue_index" src="https://user-images.githubusercontent.com/38872854/59583683-fb200b00-9116-11e9-80d3-38c6f9186a1b.png">

🎉🎉🎉🎉🎉🎉
