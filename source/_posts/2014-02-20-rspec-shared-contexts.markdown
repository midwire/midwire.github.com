---
layout: post
title: "RSpec Shared Contexts"
date: 2014-02-20 11:29
comments: true
categories: [development,rspec]
---

I love [RSpec](http://rspec.info/)! Though I know Cucumber fairly well too, as a backend developer I use RSpec almost exclusively. Cucumber is better for having tests that muggles (non-programmers, executives, suits, etc.) like to execute and look at, IMHO.

I really appreciate Philippe Creux's post on [the way he uses RSpec](http://eggsonbread.com/2010/03/28/my-rspec-best-practices-and-tips/). I do all of those things as well but I have also found [shared contexts](https://www.relishapp.com/rspec/rspec-core/docs/example-groups/shared-context) to be extremely useful in helping to keep my specs [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

They are really easy to use. We typically have a `spec/support` directory in which we put shared stuff, used across more than one set of specs. I like to create a file called `shared_contexts.rb` and inside we put code like this:

``` ruby ./spec/support/shared_contexts.rb
shared_context 'authentication' do
  let(:user) { login_user(FactoryGirl.create(:user)) }
  let(:auth_params) do
    {
      public_key: Settings["api_keys"]["public"],
      app_token:  ControllerMacros.generate_app_token,
      user:       {remember_token: user.authentication_token},
      format:     :json
    }
  end

  def login_different_user(user)
    login_user(user)
    auth_params[:user] = {remember_token: user.authentication_token}
  end
end
```

Then, in your actual specs, you can do things like this:

``` ruby
require 'spec_helper'

describe Api::V3::PhotoCommentsController, 'Actions' do
  include_context 'authentication'
  ...
  context 'on POST to #create' do
    let(:new_comment) do
      {comment: 'created from rspec'}
    end

    it "does not allow non-related user to post a comment" do
      login_different_user(FactoryGirl.create(:user))
      expect {
        post :create, auth_params.merge(new_comment)
      }.to change(GalleryComment, :count).by(0)
      response.response_code.should == 401 # not authorized
    end
  end
end
```

If we didn't use shared contexts, we would have to repeat the `login_different_user` method declaration and the necessary `let` variables in every spec that uses them.

[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) is a fundamental principle that keeps code maintainable and with fewer bugs. Just do it!

-- Midwire
