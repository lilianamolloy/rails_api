# Notes

## Creating basic rails API app

```
$ rails new bookshelf --api
$ cd bookshelf
$ rails g scaffold Book title isbn author price:integer
```

In the routes.rb  

```ruby
resources :books, defaults: {format: :json}
```
Populate the database using the seed file

```
$ rails db:migrate
$ rails db:seed
```

In the gem file 

un-comment the corse gem 
```ruby
gem 'rack-cors'
```

```
$ bundle
```
Re-start server


In config/initializers/cors 

un-comment the method and add the correct localhost
```ruby
Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do
    origins 'localhost:5500'

    resource '*',
      headers: :any,
      methods: [:get, :post, :put, :patch, :delete, :options, :head]
  end
end
```

## Using Rest Client - VS code extension

In test foleder add http folder and books.http file within

In books.http:

```http
GET http://localhost:3000

###

GET http://localhost/books

```

Click "Send Requst" which will appear above the get request