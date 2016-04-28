---
layout: post
title: "Elixir - Time Ago In Words"
date: 2016-04-28 12:50:19 -0500
comments: true
categories: elixir, phoenix
---
After reading the excellent book ["Programming Elixir"](http://amzn.to/1YVPWVr), by Dave Thomas, and ["Programming Phoenix"](http://amzn.to/1YVQbQh), by Chris McCord, Bruce Tate and José Valim, I decided to dive in.

As of this post, I am currently writing an Elixir app using the Phoenix framework. It is called [Tunedrop](http://songdrop.herokuapp.com/) and I am working on it for two reasons:

1. To learn Elixir and Phoenix
2. To share some of the music that I grew up on with my kids

You can see the code [here](https://github.com/cblackburn/tunedrop).

It is definitely a work in progress and may look pretty raw at times. However, I wanted to share how easy it is to port code from Ruby to Elixir for your benefit, happiness and profit.

As I play music in iTunes, Tunedrop dynamically posts the song's artist, name and year released, along with the time it was played. Originally, the time played was absolute and looked like this: `4/12 15:32`. I wanted to look something like the Rails [`ActionView::Helpers.distance_of_time_in_words`](https://github.com/rails/rails/blob/97f2c4129ae23ee074986a588628acc689a86462/actionview/lib/action_view/helpers/date_helper.rb#L71):

![listings](../images/tunedrop_listings.png)

Here's how I did it:

## Preparation

I'm using the [`timex`](https://github.com/bitwalker/timex) Elixir library for DateTime manipulations. I followed the directions there to install it into my Phoenix project.

## TimeHelpers

### The Tests

In [`tunedrop/test/views/time_helpers_test.exs`](https://github.com/cblackburn/tunedrop/blob/master/test/views/time_helpers_test.exs) <- click the link to view the entire test module.

```elixir
defmodule Tunedrop.TimeHelpersTest do
  use Tunedrop.ViewHelperCase
  use Timex

  test "returns time in words for now" do
    time = DateTime.now
    words = Tunedrop.TimeHelpers.distance_of_time_in_words(time)
    assert words =~ ~r/Less than 1 minute/
  end

  test "returns time in words for 30 minutes" do
    time = DateTime.shift(DateTime.now, minutes: 30)
    words = Tunedrop.TimeHelpers.distance_of_time_in_words(time)
    assert words =~ ~r/30 minutes/
  end

  ...
end
```

### The Module

In [`tunedrop/web/views/time_helpers.ex`](https://github.com/cblackburn/tunedrop/blob/master/web/views/time_helpers.ex) <- click the link to view the entire module.

```elixir
defmodule Tunedrop.TimeHelpers do
  use Timex
  alias Timex.DateTime

  @moduledoc """
  Helpers for DateTime display
  """

  @doc """
  Generates approximate distance of time between two times in words.
  """
  def distance_of_time_in_words(from_time, to_time \\ DateTime.now) do
    case from_time > to_time do
      true ->
        from = to_time
        to = from_time
      false ->
        from = from_time
        to = to_time
    end
    distance_in_seconds = abs(DateTime.to_seconds(to_time) - DateTime.to_seconds(from_time))
    distance_in_minutes = abs(round(distance_in_seconds / 60.0))

    words = case distance_in_minutes do
      n when n in 0..1 ->
        "Less than 1 minute"
      n when n in 2..45 ->
        "#{n} minutes"
      n when n in 45..90 ->
        "about 1 hour"
      n when n in 90..1440 ->
        "about #{round(n / 60.0)} hours"
      n when n in 1440..2520 ->
        "about 1 day"
      n when n in 2520..43200 ->
        "about #{round(n / 1440.0)} days"
      n when n in 43200..86400 ->
        "about #{round(n / 43200.0)} months"
      n when n in 86400..525600 ->
        "#{round(n / 43200.0)} months"
      _ -> "a long time"
    end
    words
  end
end

```

I'm sure this code could be better, but what I'm impressed with is how easy it is to port code from Ruby into the pattern-matching paradigm of Elixir, and how similar it looks to the [original Ruby code](https://github.com/rails/rails/blob/97f2c4129ae23ee074986a588628acc689a86462/actionview/lib/action_view/helpers/date_helper.rb#L71).
