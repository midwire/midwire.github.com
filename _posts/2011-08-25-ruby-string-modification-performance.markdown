---
layout: post
title: "Ruby String Modification Performance"
date: 2011-08-25 16:56
comments: true
categories: [ruby,strings,performance,profiling]
---
Having used many programming languages over the years; when I began using Ruby I expected to find that string interpolation performance would be slow and similar to other languages.  I was surprised!

In Ruby, 1.8.x versions, string interpolation is always faster.  Here are the timings:

{% highlight ruby %}
Profiler.time_this("Single Quotes (+ operator at end):") {
  x = ''
  (0..MAX).each do |i|
    x = 'This is a test ' + i.to_s
  end
}

Profiler.time_this("Single Quotes (+ operator in middle):") {
  x = ''
  (0..MAX).each do |i|
    x = 'This is a test ' + i.to_s + 'x'
  end
}

Profiler.time_this("Single Quotes (<< operator at end):") {
  x = ''
  (0..MAX).each do |i|
    x = 'This is a test ' << i.to_s
  end
}

# Very slow
Profiler.time_this("Single Quotes: (<< operator in middle)") {
  x = ''
  (0..MAX).each do |i|
    x = 'This is a test ' << i.to_s << 'x'
  end
}

Profiler.time_this("Double Quotes (interpolation at end):") {
  x = ""
  (0..MAX).each do |i|
    x = "This is a test #{i}"
  end
}

Profiler.time_this("Double Quotes (interpolation in middle):") {
  x = ""
  (0..MAX).each do |i|
    x = "This is a test #{i}x"
  end
}
{% endhighlight %}

Produces...

    Timings for [Single Quotes (+ operator at end):]
    Thread ID: 2148446640
    Total: 0.785381

     %self     total     self     wait    child    calls  name
     59.14      0.79     0.46     0.00     0.32        1  Range#each (ruby_runtime:0}
     22.29      0.18     0.18     0.00     0.00   100001  Fixnum#to_s (ruby_runtime:0}
     18.57      0.15     0.15     0.00     0.00   100001  String#+ (ruby_runtime:0}
      0.00      0.79     0.00     0.00     0.79        1  <Class::Midwire::Profiler>#time_this (/Users/midwire/Source/ruby/ruby-profiles/lib/midwire/profiler.rb:12}
      0.00      0.00     0.00     0.00     0.00        1  <Class::Object>#allocate (ruby_runtime:0}



    Timings for [Single Quotes (+ operator in middle):]
    Thread ID: 2148446640
    Total: 1.094465

     %self     total     self     wait    child    calls  name
     57.92      1.09     0.63     0.00     0.46        1  Range#each (ruby_runtime:0}
     26.46      0.29     0.29     0.00     0.00   200002  String#+ (ruby_runtime:0}
     15.62      0.17     0.17     0.00     0.00   100001  Fixnum#to_s (ruby_runtime:0}
      0.00      1.09     0.00     0.00     1.09        1  <Class::Midwire::Profiler>#time_this (/Users/midwire/Source/ruby/ruby-profiles/lib/midwire/profiler.rb:12}
      0.00      0.00     0.00     0.00     0.00        1  <Class::Object>#allocate (ruby_runtime:0}



    Timings for [Single Quotes (<< operator at end):]
    Thread ID: 2148446640
    Total: 0.806073

     %self     total     self     wait    child    calls  name
     55.94      0.81     0.45     0.00     0.36        1  Range#each (ruby_runtime:0}
     22.95      0.18     0.18     0.00     0.00   100001  Fixnum#to_s (ruby_runtime:0}
     21.11      0.17     0.17     0.00     0.00   100001  String#<< (ruby_runtime:0}
      0.00      0.81     0.00     0.00     0.81        1  <Class::Midwire::Profiler>#time_this (/Users/midwire/Source/ruby/ruby-profiles/lib/midwire/profiler.rb:12}
      0.00      0.00     0.00     0.00     0.00        1  <Class::Object>#allocate (ruby_runtime:0}



    Timings for [Single Quotes: (<< operator in middle)]
    Thread ID: 2148446640
    Total: 1.090110

     %self     total     self     wait    child    calls  name
     55.56      1.09     0.61     0.00     0.48        1  Range#each (ruby_runtime:0}
     27.31      0.30     0.30     0.00     0.00   200002  String#<< (ruby_runtime:0}
     17.12      0.19     0.19     0.00     0.00   100001  Fixnum#to_s (ruby_runtime:0}
      0.00      1.09     0.00     0.00     1.09        1  <Class::Midwire::Profiler>#time_this (/Users/midwire/Source/ruby/ruby-profiles/lib/midwire/profiler.rb:12}
      0.00      0.00     0.00     0.00     0.00        1  <Class::Object>#allocate (ruby_runtime:0}



    Timings for [Double Quotes (interpolation at end):]
    Thread ID: 2148446640
    Total: 0.567917

     %self     total     self     wait    child    calls  name
     65.52      0.57     0.37     0.00     0.20        1  Range#each (ruby_runtime:0}
     34.48      0.20     0.20     0.00     0.00   100001  Fixnum#to_s (ruby_runtime:0}
      0.00      0.57     0.00     0.00     0.57        1  <Class::Midwire::Profiler>#time_this (/Users/midwire/Source/ruby/ruby-profiles/lib/midwire/profiler.rb:12}
      0.00      0.00     0.00     0.00     0.00        1  <Class::Object>#allocate (ruby_runtime:0}



    Timings for [Double Quotes (interpolation in middle):]
    Thread ID: 2148446640
    Total: 0.580440

     %self     total     self     wait    child    calls  name
     67.23      0.58     0.39     0.00     0.19        1  Range#each (ruby_runtime:0}
     32.77      0.19     0.19     0.00     0.00   100001  Fixnum#to_s (ruby_runtime:0}
      0.00      0.58     0.00     0.00     0.58        1  <Class::Midwire::Profiler>#time_this (/Users/midwire/Source/ruby/ruby-profiles/lib/midwire/profiler.rb:12}
      0.00      0.00     0.00     0.00     0.00        1  <Class::Object>#allocate (ruby_runtime:0}

Regards,

-- Midwire
