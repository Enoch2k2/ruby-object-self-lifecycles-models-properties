# Ruby OO Lifecycles, Models, Properties, Self
-  [Notes](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#notes)
    - [learn what an object is](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#learn-what-an-object-is)
    - [Ruby Vocabulary](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#ruby-vocabulary)
    - [learn what instance methods are (bark)](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#learn-what-instance-methods-are-bark)
    - [learn what instance variables are (name)](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#learn-what-instance-variables-are-name)
    - [learn how to access instance variables outside of the class](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#learn-how-to-access-instance-variables-outside-of-the-class)
    - [learn about the lifecycle of an object, when an object is born, how do we access it after it's been instantiated so that it isn't lost after creation](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#learn-about-the-lifecycle-of-an-object-when-an-object-is-born-how-do-we-access-it-after-its-been-instantiated-so-that-it-isnt-lost-after-creation)
    - [learn about class scopes and difference between class scopes and instance scopes, class methods vs instance methods how to call each one, and about the value of self in a class method vs self in an instance method.](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#learn-about-class-scopes-and-difference-between-class-scopes-and-instance-scopes-class-methods-vs-instance-methods-how-to-call-each-one-and-about-the-value-of-self-in-a-class-method-vs-self-in-an-instance-method)
- [Examples](https://github.com/Enoch2k2/ruby-object-self-lifecycles-models-properties#examples)
## **Notes** ##
### learn what an object is
  - An object is a source of actions and properties
  - An object can describe a real life object, such as a person, a pet, food, etc... Anything we see we can turn to code.

### Ruby Vocabulary
  - instantiate: creating a new object
  - instance: refers to a unique object created from a class

### learn how to create an object (Dog)
### learn what instance methods are (bark)
  - Instance Method: An actionable method that only an instance can call. Can also be used to retrieve object properties or set them.
### learn what instance variables are (name)
  - Instance Variables: Variables that are known throughout the class in every instance method.
### learn how to access instance variables outside of the class
  - Writer Method: A method used to set an instance variable, to  give a property to an object.
  - Reader Method: A method used to return an instance variable's value, to retrieve an object property.
### learn about the lifecycle of an object, when an object is born, how do we access it after it's been instantiated so that it isn't lost after creation
  - initialize method: Where you set base values for all of your properties. What you want to happen as soon as you instantiate your object. (ex: dog.bark, the one unique instance of dog would bark)
### learn about class scopes and difference between class scopes and instance scopes, class methods vs instance methods how to call each one, and about the value of self in a class method vs self in an instance method.
  - self: refers to what is calling the method you place self inside. Self refers to the class in a class method, self refers to the instance in an instance method.
  - class method: A Method that the class itself calls, an instance method cannot call these methods. (ex: Dog.all would retrieve all the dog instances).

### think about real life example of an object's use
### BONUS: create a find_by class method
### BONUS: create a find_or_new_by class method

## **Examples** ##