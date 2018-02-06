---
layout: post
title: "Update ActiveRecord Instance With Validation Context"
date: 2018-02-06 08:17:14 -0600
comments: true
categories: [development,ruby,rails]
---
Validation contexts are really useful, however only the methods `valid?` and `save` allow you to pass a custom validation context. What about `update`?

If you want to pass a validation context when calling `update` on an Active Record model instance, add this to your base class, which is `ApplicationRecord` by default in Rails 4.x and 5.x.

```ruby
class ApplicationRecord < ActiveRecord::Base
  self.abstract_class = true

  def update_with_context(new_attributes, context)
    with_transaction_returning_status do
      assign_attributes(new_attributes)
      save(context: context)
    end
  end
end
```
