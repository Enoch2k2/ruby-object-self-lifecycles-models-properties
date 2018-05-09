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
  - **instantiate**: creating a new object
  - **instance**: refers to a unique object created from a class

### learn how to create an object (Dog) (See Examples)
### learn what instance methods are (bark)
  - **Instance Method**: An actionable method that only an instance can call. Can also be used to retrieve object properties or set them.
### learn what instance variables are (name)
  - **Instance Variables**: Variables that are known throughout the class in every instance method.
### learn how to access instance variables outside of the class
  - **Writer Method**: A method used to set an instance variable, to  give a property to an object.
  - **Reader Method**: A method used to return an instance variable's value, to retrieve an object property.
  - **attr_reader**: A class attribute method that gives a reader method for each symbol associated to it.
  - **attr_writer**: A class attribute method that gives a writer method for each symbol associated to it.
  - **attr_accessor**: A class attribute method that gives both a writer and a reader method for each symbol associated to it.
### learn about the lifecycle of an object, when an object is born, how do we access it after it's been instantiated so that it isn't lost after creation
  - **initialize method**: Where you set base values for all of your properties. What you want to happen as soon as you instantiate your object. (ex: dog.bark, the one unique instance of dog would bark)
### learn about class scopes and difference between class scopes and instance scopes, class methods vs instance methods how to call each one, and about the value of self in a class method vs self in an instance method.
  - **self**: refers to what is calling the method you place self inside. Self refers to the class in a class method, self refers to the instance in an instance method.
  - **class method**: A Method that the class itself calls, an instance method cannot call these methods. (ex: Dog.all would retrieve all the dog instances).
  - **class variable**: A variable defined that only the class (should) knows about.

### think about real life example of an object's use
### BONUS: create a find_by class method
### BONUS: create a find_or_new_by class method

## **Examples** ##
```
class Dog
  attr_accessor :name
  attr_reader :breed, :treats
  
  @@all = []
  
  # instance method that's called as soon as an instance is born
  def initialize(name, breed)
    # self refers to instance
    self.name = name
    @breed = breed
    @treats = []
    self.save
  end
  
  #instance method (actionable) bark
  def bark
    puts "woof!"
  end
  
  def details
    puts "The dogs name is #{self.name} and it's breed is #{self.breed}"
  end
  
  def save
    #self refers to the instance
    # .class refers to the instance's class
    # .all refers to the class variables return value (array)
    self.class.all.push(self)
  end
  
  def self.all
    @@all
  end
  
  # writer method
  # def name=(name)
  #   # instance variable = value
  #   @name = name
  # end
  
  # reader method
  # def name
  #   @name
  # end
end

#variable = Class.new for creating a new instance of that class, will run initialize with any arguments passed in

# dog = Dog.new("Fido", "Shitzu")
# dog.name = "Sally" (dogs name is now Sally) example of using writer method
# dog.details (gives us back the details of the dog), example of using an instance method
# Dog.new("Lassie", "Golden Retriever")
# Dog.new("Butch", "Mutt")
# Dog.all.each do |dog|
#   dog.details
# end
```
Real life example of a User
```
class User
  attr_accessor :username, :password, :logged_in
  attr_writer :email
  
  @@all = []
  
  def initialize(email, username, password)
    self.email = email
    self.username = username
    self.password = password
    self.save
  end
  
  def save
    self.class.all.push(self)
  end
  
  def self.all
    @@all
  end
  
  def self.find_by_username(username)
    self.all.detect{|user| user.username == username }
  end
  
  def self.login(username, password)
    user = User.find_by_username(username)
    if user.nil?
      puts "Cannot find user by that username"
    elsif user.password != password
      puts "Does not match password"
    else
      puts "successfully logged in"
      user.logged_in = true
    end
  end
  
end

User.new("test@test.com", "test", "testtest")

User.login("test", "testtest")
```