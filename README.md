# Workshops application

Hi! We think it’s great that you want to **join along with Netguru** to start learning **Ruby on Rails**. Taking part in workshops is also a **great opportunity to start an internship** with us and become one of the Netguru folks. Since you have just taken your first step on your adventure with programming in RoR, we challenge you to complete the following task. **Ready, steady…Go!**

### Let’s start with a setup:

**Database**

Copy the database config file (and edit if needed): 
` cp config/database.yml.sample config/database.yml`

Make sure the user you've listed in `database.yml` is created for postgres:
`createuser -s -r workshops`

Setup the database for your application (development and test environments):
`bin/rake db:setup`
`bin/rake db:test:prepare`

*Optional: use [guard](#improve-your-workflow-with-automated-rspec-running) in order to improve your workflow*

### Issues to solve:

1. There are a few missing fields on the `User` model. Make sure `spec/models/user_spec.rb passes.`

2. Make sure settings for [devise](https://github.com/plataformatec/devise) are
   configured properly.  If they aren’t, most of the controller specs will fail: 
  * Most of the configuration changes require the server to be restarted.
  * At some point **you'll have to overwrite the default devise views** - you can find all the required info in the gem readme.
  
3. Check `spec/controllers/categories_controller_spec.rb` - there should be a
   couple errors on actions checking admin presence.

4. Next up: `Product` model and `spec/models/product_spec.rb`. Play with validations a bit, calculate average rating and you'll be good to go.

5. Fix specs for `Category` model.

6. Fix specs for `Review` model.

7. You'll have to deal with `ProductsController`. Again, you'll have to check for permissions. Only a product owner should be able to make changes. Make sure to give the user a proper message when they try to perform forbidden actions.

8. Make sure `ReviewDecorator` is used properly, There's one action which needs to be declared there. See `spec/decorators/review_decorator_spec.rb` for details.

9. Check if each review is assigned to user who wrote it.

10. If some actions (like links to edit a page, create a new one) are not allowed for a particular user then please hide them in a template (for example with `if`).

11. In navigation bar insert links for guest users to login / signup and for users that are already logged in - to logout.

12. Don't forget to check if application works in the browser :).

13. Unleash your design skills. Add some CSS to the application to make it prettier (we won't say it's ugly, but you know, it's not a beauty [YET!]). Please use [Bootstrap 3](http://getbootstrap.com/css/) for styling, which is already added to application. Psss! Don't forget about styling `devise` views :).

14. Create user profile page (using Boostrap 3). Use your imagination about what should go there. You can start with name, email, etc.

15. On user profile list 5 last user's reviews with formated date (dd-mm-yy).

16. Fill `seeds.rb` with 5 accounts for user and one admin account to login and example category with products and reviews.

17. Make sure your project is available on Heroku with **seeds data**.

## What disqualifies your application

1. Tests are not passing.

2. Website doesn't work on Heroku.

3. Design is not finished.

### Here are some great resources to help you with kicking off your adventure with Ruby and Rails:

* [http://www.codeschool.com/paths/ruby](http://www.codeschool.com/paths/ruby) - free Ruby and Rails courses available at the elementary level
* you want to be sure your Ruby basis are solid? Check out the Ruby Koans - [http://rubykoans.com/](http://rubykoans.com/)
* [http://guides.rubyonrails.org/](http://guides.rubyonrails.org/) - sooner or later this one will come in handy
* not feeling comfortable with JavaScript / jQuery? CodeSchool can help you with this one too - [http://www.codeschool.com/courses/try-jquery](http://www.codeschool.com/courses/try-jquery)


### Improve your workflow with automated rspec running

Technically, they way how you will be completing part of this app is called [Test-driven development (TDD)](http://stackoverflow.com/questions/11941/getting-started-with-agile-and-tdd). I found using [guard gem](https://github.com/guard/guard) in this programming methodology is very helpful. If you aren't familiar with TDD concept yet let me explain this in few words.

Idea of this programming methodology is to first write a test and then write a piece of code that will make this test pass :green_heart:.

In `Workshops` app tests are already written. The 'only' thing you need to do is to make these tests pass and eventually add your own for custom behaviour of app (and also make them pass!). 

To make this process more friendly I would recommend you use [guard-rspec gem](https://github.com/guard/guard-rspec). How does it work?

It's very simple. By default Guard (with `rspec` addon) watches files in your working folder and when you make any change to them (add piece of code, remove file, etc.) it runs test so you can track your progress all the time without running `rspec` command anymore! 

It saves a lot of the time, help to track current and further tasks and what is more, if your new piece of code will destroy (bug :exlamation:) any behaviour in app you will get notified about it immediately. As sooner you can react on bug as easier it is to remove this bug.

How to start? 

1. Open new tab/window of console/terminal/cmd that will be dedicated for guard runner.
2. Go to `Workshops` directory and run `guard init rspec`

    You should see in console:

    ```
    21:02:07 - INFO - Writing new Guardfile to /path_where_you_cloned_this_repo/workshops/Guardfile
    21:02:07 - INFO - rspec guard added to Guardfile, feel free to edit it
    ```

3. Run `guard` command. Now this console/terminal/cmd tab will watch all files in project's directory untill you terminate it (`control+c on OS X`). You should see this console output:

    ```
    21:02:18 - INFO - Guard is using TerminalTitle to send notifications.
    21:02:18 - INFO - Guard::RSpec is running
    21:02:18 - INFO - Guard is now watching at '/path_where_you_cloned_this_repo/workshops'
    ```

4. Go write some code and get notified about your progress on live with guard!

You can also modify default behaviour of guard! For further read visit [guard-rspec repo](https://github.com/guard/guard-rspec) and/or [guard repo](https://github.com/guard/guard).

Also if you want to take full adventage of `Rails 4.1` you should consider using `spring` with `RSpec`. Further reading [here](http://girders.org/blog/2014/02/06/setup-rails-41-spring-rspec-and-guard/)

## Good Luck! 

**Psst! Do not hesitate to ask your questions on [hipchat](https://www.hipchat.com/gElgOYCSJ)**
**And check out event on [facebook](https://www.facebook.com/events/457911497684273/).**
