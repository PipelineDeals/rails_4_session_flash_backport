# Rails4SessionFlashBackport
[![Gem Version](https://badge.fury.io/rb/rails_4_session_flash_backport.png)](http://badge.fury.io/rb/rails_4_session_flash_backport)
[![Build Status](https://travis-ci.org/envato/rails_4_session_flash_backport.png)](https://travis-ci.org/envato/rails_4_session_flash_backport)

Different versions of Rails have stored flash messages in different objects in
the session, making it a pain to upgrade without nuking everyones session. The
good ol' `ActionDispatch::Session::SessionRestoreError` making life difficult.

This gem was created because we wanted to be able to keep our users Rails 2
sessions working on Rails 3, and we figured as long as we're going to be doing
crazy stuff we might as well go and use the far more sensible practice from
Rails 4 of storing the flash as basic ruby types.

For more details of the how and why, check out our blog post 
[Happily upgrading Ruby on Rails at production scale](http://webuild.envato.com/blog/upgrading-ruby-on-rails-at-production-scale/)

When using this gem on a Rails 2 or 3 app:

 - Flash messages are stored as basic objects in the Rails 4 style.
 - Flash messages in the Rails 2 format can be successfully decoded.
 - Flash messages in the Rails 3 format can be successfully decoded.
 - Flash messages in the Rails 4 format can be successfully decoded.

Additionally, on Rails 2 we include some patches for the SessionHash and
CookieStore in order to make them act more like a HashWithIndifferentAccess,
like the versions on Rails 3, so that your session_id can survive a trip to
Rails 3 and back.

This actually makes it possible to bounce requests from a Rails 2 server, to a
Rails 3 server and back again so long as both servers are using this gem. Very
helpful when you're doing a big Rails 2 => 3 upgrade and want to run a few
Rails 3 servers concurrently with your Rails 2 cluster to verify everything is
fine and performance is acceptable without
having to do the all-in switch.

_Please Note_ this gem is not intended to be loaded in Rails 4. If you're using
Rails 4, you've already got all of this gem's functionality!

## Installation

Add this line to your application's Gemfile:

    gem 'rails_4_session_flash_backport'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install rails_4_session_flash_backport

Copyright
---------

Copyright (c) 2012 [Envato](http://envato.com), [Lucas Parry](http://github.com/lparry), [chendo](http://github.com/chendo). See LICENSE.txt for further details.

