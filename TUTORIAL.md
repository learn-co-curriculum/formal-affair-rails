# Guide to Solving Formal Affair Rails


The purpose of this lab is to create 3 separate forms and use ```ruby
protect_from_forgery with: :exception``` to protect against cross site forgery.
The models and controllers are already set up to handle your HTTP requests. 

###FORMS:
One form for each of your models.

* Babies \_form partial uses the ```form_for``` helper.

Creating the form, you already have access to @baby from the controller. Now construct the ```form_for @baby``` for all of its attributes: first\_name, last\_name, weight, birth\_date. Don't forget the submit button.

```form_for``` binds the form to a model object. This is typically used for editing or creating an instance of an object.

* Concretes edit and new views use ```form_tag``` helper

```form_tag``` can be used to make a "PATH" and "DELETE" request since most browsers only support "GET" and "POST". 
Using this tag is how you can hack the form and override the method from a "POST" request to "PATCH" or "DELETE".

```ruby
form_tag(search_path, method: "patch")
```

* Searches uses standard HTML ```<form>``` tags

Regular HTML form.

```html
<form action="/searches" method="post">
  <input name="authenticity_token" type="hidden" value="<%= form_authenticity_token %>" />
  <input type="text" name="q">
  <input type="submit" value="Search">
</form>
```

### CSRF
You must add ```ruby
protect_from_forgery with: :exception``` in your ApplicationController.



