---
layout: post
title:      "Secure with Validations!"
date:       2021-02-17 01:14:32 -0500
permalink:  secure_with_validations
---



Secure with Validations!

We use **Validation** to ensure that only valid data is saved in your database. Without validations, our database will save all types of wonky data. There are many ways to validate that come along with specific procedures, such as (database constraints, client-side validations, controller-level validations, and model-level validations).

In this case, applying the model level validations is the best one to ensure that only valid data is saved into your database. Active Record is magic! It handles the M-model of the MVC paradigm, which makes it easy to use, rails provides you with built-in helpers for common needs, it also allows you to create your own validation methods as well. Nice!

```
 class User < ApplicationRecord
      has_many :posts, dependent: :destroy
# end
```
 
This class User has a *has_many relationship to** : post*, and the **dependent: : destroy** is also assigned to has_many relationship. This means that all the post that belongs to a User should be deleted if that user is deleted.
 
If the client fills out a form to the application, you don't want just any information saved to the database that is not valid to what the form is requesting. That is where **Active Record** validations come in. As I said before Validations can be used in different ways, but the best place to start is helpers that Active Record provides you with. 
 
With one line of code, you can validate a whole form. *That's magic*! To be a little more specific these helpers are set to provide common use validations such as; a required field, an entry that requires the length of a character, or a certain text field like an email. Below you see that user attributes being validated by *presence* with a condition *true.*  This validation checks that the required field is not left blank. 
 
 Another very useful validation helper is the *uniqueness validator*. This checks to make sure the database does not already contain the submitted value (: username). To specify it makes sure that only one user can have a specific username.
 
 ```
`# user.rb
class User < ApplicationRecord

  has_many :posts, dependent: :destroy
	
  validates :username, :password, :bio, presence: true
	validates :username, uniqueness: true
end`
```

You can also customize your error messages that are sent to the client-side, by adding to a message in the place of the condition true, in dynamic interpolation the value being validated with percent sign notation {}. Say if a user wanted to be assigned their: username *Angel203*, but the username already exists in the database, that custom message will return.

```
# user.rb

class User < ApplicationRecord

  has_many :posts, dependent: :destroy
validates :username, :password, :bio, presence: true
validates :username, uniqueness: 
  {message: 'An account associated with %{value} already exists'}
	
end

```

```
username An account associated with *Angel203* already exists
```
This is just a part of what validations in Active record can do. But the beauty of it you can validate your whole application  (MVC) to be secured for the clients' end. 
For more information look up documentation. I hope this was good information for you.


