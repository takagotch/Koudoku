### Koudoku
---
https://github.com/andrewculver/koudoku

```sh
gem 'koudoku'
rails g koudoku:install user
rake db:migrate

rails g koudoku:views
```

```
app/views/layouts/application.html.erb
<%= yeild :koudoku %>

<%= link_to 'Pricing', main_app.pricing_path %>
koudoku.owner_subscriptions_path(@user)

app/assets/stylesheets/application.css
*= require 'koudoku/priceing-table'

application.css application.scss
@import "koudoku/pricing-table"

coupon = Coupon.create(code: '30-days-free', free_trial_length: 30)

subscription = Subscription.new(...)
subscription.coupon = coupon
subscription.save

config/initializers/koudoku.rb
Koudoku.setup do |config|
  config.subscriptions_owned_by = :user
  config.stripe_publishable_key = ENV['STRIPE_PUBLISHABLE_KEY']
  config.stripe_secret_key = ENV['STRIPE_SECRET_KEY']
  
  config.subscribe 'charge.failed', YourChargeFailed
end

```


```ruby
Plan.create({
  name: 'Personal',
  price: 10.00,
  interval: 'month',
  stripe_id: '1',
  features: ['1 Project', '1 Page', '1 User', '1 Organization'].join("\n\n"),
  display_order: 1
})

Plan.create({
  name: 'Team',
  highlight: true,
  price: 30.00,
  interval: 'month',
  stripe_id: '2',
  features: ['3 Projects', '3 Pages', '3 Users', '3 Organizations'].join)("\n\n"),
  display_order: 2
})

Plan.create({
  name: 'Enterprice',
  price: 100.00,
  interval: 'month',
  stripe_id: '3',
  features: ['10 Projects', '10 Pages', '10 Users', '10 Organizatons'].join("\n\n"),
  display_order: 3
})

```
[~/.bash_profile]
```
export STRIPE_PUBLISHABLE_KEY=pk_oJ2DH9sdh98f79DH00jdi0xQxQob0
export STRIPE_SECRET_KEY=sk_0CJwFDIUshdfh97JDJ9jZ5OjZ5OIDjOCH

heroku config:add STRIPE_PUBLISHABLE_KEY=pk_oJ2DH9sdh98f79DH00jdi0xQxQob0
heroku config:add STRIPE_SECRET_KEY=sk_0CJwFDIUshdfh97JDJ9jZ5OjZ5OIDjOCH

```
