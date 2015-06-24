# Rails-Lite
A web framework inspired by the router and controller system of Ruby on Rails, built
on top of a WEBrick server.

To use, put controllers in lib inheriting from controller_base, a list of desired 
routes for those controllers in bin/router_server.rb (either per HTTP method, or 
using the router#resources helper), and any needed html.erb views in views.

## ControllerBase
Similar to Rails ActionController::Base, serves a base class for different 
controllers. Contains the logic for building a HTTP response, whether an html page 
or a redirect. 

It also uses two helper classes, Session and Flash, to manage browser cookies, reading
any that are present in the request and providing an interface to change them.

## Router
Parses the list of routes into regular expressions, that are stored and matched with
incoming HTTP requests, and either instatiates an appropriate controller and calls an
appropriate method, or builds and returns a 404-response. Parses any route parameters
using capture groups and passes them into the controller.

It also checks the parameter with a _method key, and if it sees one, it changes the
HTTP request method to match before passing it on to the controller.

## HTMLHelper
A module containing link_to and button_to helper methods which, like the ones in Rails,
simplify creation of links and single-button froms in views.
