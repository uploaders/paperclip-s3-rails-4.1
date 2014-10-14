# PaperClip - Example
## By:
### Forrest Parker
### Phillip Nguyen

Gems:
  gem 'paperclip'
  gem 'aws-sdk'

## Step by Step guide!

- `$ rails new pclip-example`
- add gems to gem file
- `$ bundle`
- `$ rails g scaffold article title:string body:text`
- In config/routes.rb
    set your 'root articles#home'
- $ `rails g migrations addattachmentimagetoarticles`
    this should generate a file kind of like this.

    `class AddAttachmentToUsers < ActiveRecord::Migration
      def change
        add_attachment :users, :avatar
      end
    end`

- In app/views/articles/_form.html.erb
  add this line somewhere
    `<%= f.file_field :image %>`

- In app/views/articles/show.html.erb
  add this line somewhere
    `<%= f.file_field :image %>`

- In config/environments/development.rb
  add this to set up aws keys and stuff (notice the url listed in the bucket, you
  will likely change it to your bucket name with the region you are set up in.)
  ALSO! DO NOT HARDCODE YOUR KEYS HERE!

  `config.paperclip_defaults = {
    :storage => :s3,
    :s3_credentials => {
      :bucket => 'cw-example.s3-website-us-west-2.amazonaws.com',
      :access_key_id => ENV['AWS_ACCESS_KEY_ID'],
      :secret_access_key => ENV['AWS_SECRET_KEY']
    }
  }`

Happy Coding and Thanks!


