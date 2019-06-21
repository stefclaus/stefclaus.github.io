---
layout: post
title:      "Tips For Implementing Facebook OAuth With An Existing Signin"
date:       2019-06-21 14:02:43 +0000
permalink:  tips_for_implementing_facebook_oauth_with_an_existing_signin
---


I want to walk you through some of the steps I took to implement Facaebook OAuth as a part of my project. 

Facebook OAuth seemed tricky at first, but with a little persistence, I was able to incorporate Facebook logon into my project. The first time I successfully logged in with one click and saw "Welcome, Stef Claus!" was magical. 

**Here's some tips and tricks I learned in implementing Facebook OAuth to a project with an existing login:
**

I got most of the way through the Facebook OAuth implementation by carefully following the[ Learn tutorial](https://learn.co/tracks/full-stack-web-development-v7/rails/authentication/omniauth). I'd highly recommend you carefully reread this section if you are trying to do implement Facebook OAuth! Using the tutorial, I was able to create my Facebook app, get my Facebook app credentials, and set up my omniauth.rb file inside config/initializers.

After the tutorial, I needed to make two key changes to make the project work with my existing project. 

-First, I needed to created a new column in my users database to accomodate the uid from Facebook. I created this retroactively using a generator and the command 

```
rails g migration add_uid_to_users uid:string --no-test-framework

```

The finished migration looks like this: 

```
class AddFacebookColumnToAssistant < ActiveRecord::Migration[5.2]
  def change
    add_column :assistants, :uid, :string
  end
end

```

Second, I had to implement the Facebook OAuth create method in my sessions controller. I already had a create method for my standard login process--and it worked great! And I had the code for the Facebook creatae method from the walkthrough. How to reconcile them both so users logging in via Facebook would get routed through the Facebook create method, and standard users would get pointed through the standard create method?

As it turns out, this is super easy to implement! I kept my facebook create code, but I just tweaked the name:

```
  def fbcreate
    @user = User.find_or_create_by(uid: auth['uid']) do |u|
      u.name = auth['info']['name']
      u.email = auth['info']['email']
      u.image = auth['info']['image']
      u.password = SecureRandom.hex(15)
    end
    session[:user_id] = @user.id
    redirect_to user_path(@user)
  end
```

I also added this route to my routes file: 

```
  get '/auth/facebook/callback' => 'sessions#fbcreate'

```


I've really enjoyed my time with rails--so much magic!-- and I hope I get the chance to use it professionally. 


