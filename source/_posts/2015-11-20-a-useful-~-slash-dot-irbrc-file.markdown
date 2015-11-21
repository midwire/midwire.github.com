---
layout: post
title: "A Useful ~/.irbrc File"
date: 2015-11-20 22:03:49 -0600
comments: true
categories: ruby
---
Here is my `~/.irbrc` file.

{% codeblock lang:ruby ~/.irbrc %}
require 'irb/completion'

def what_methods(obj)
  (obj.public_methods - Object.public_methods - Object.instance_methods).sort
end

def wm(obj)
  what_methods(obj)
end

def predicates(obj)
  what_methods(obj).grep(/\?$/)
end

def locate(obj, method)
  obj.method(method.to_sym).source_location
end
{% endcodeblock %}

It contains 4 useful methods as follows:

## `what_methods`

Allows you to determine what methods are available on an object without displaying all of Object instance methods. The following `irb` session calls `what_methods` on an Array instance:

{% codeblock lang:ruby %}
ary = [1,2,3]
what_methods ary
=> [:&,
 :*,
 :+,
 :-,
 :<<,
 :[],
 :[]=,
 :all?,
   # ...
 :uniq,
 :uniq!,
 :unshift,
 :values_at,
 :zip,
 :|]
{% endcodeblock %}

*Note: `wm` is just a shortcut for `what_methods`, cuz I'm lazy.*

As you can see, it lists out all public instance methods for the Array instance, `ary`.

## `predicates`

Predicates is similar to `what_methods`. It actually calls `what_methods` and filters out all but methods that end with a question mark (predicates).

{% codeblock lang:ruby %}
ary = [1,2,3]
predicates ary
=> [:all?, :any?, :empty?, :member?, :none?, :one?]
{% endcodeblock %}

Pretty cool, huh?

## `locate(obj, method)`

Have you ever been at some breakpoint and wanted to look at the code for a specific method? This tiny method lets you do just that.

{% codeblock lang:ruby %}
get :index
locate response, :ok?
["/Users/midwire/Code/ruby/Rallyhood/rh_svc_analytics/vendor/bundle/ruby/2.2.0/gems/rack-1.6.4/lib/rack/response.rb", 126]
{% endcodeblock %}

How about that? It even gives you the line number along with the file where the method is defined.

To use these in an `irb` session, just copy them into your `~/.irbrc` file. However, that won't help if you plan to use them during a pry session. For that just copy them into your `~/.pryrc` file.

Enjoy!

