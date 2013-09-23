# Design Patterns

## Why?
Turns out that lots of problems that we have when are are coding are problems that many other people have had before. These people being programmers they decided to abstract ( take all of the details about how they solved it this particular time out ) and write about the pattern they used. These patterns were originally published a book called [Design Patterns](http://www.amazon.com/Design-Patterns-Object-Oriented-Professional-Computing/dp/0201634988 "Design Patterns"). They are colluquly refered to as the *gang of four* patterns due to their origins being four Computer Scientists. 

## What?
In genral there are 23 or so pattern listed in and discribed n the Design Patterns book and a few have been added here and there by industry. This week there are a few that are relevent to making high quality UIs. For the expenations of patterns this week I am going to tailor explenations to why they matter for javascript, they can and are used in other places in completely different ways but they are a bit out of scope.

## Tips
- Google is your freind USE IT!
- Wikipedia has some pretty good examples but they can get a bit sciency
- Draw pictures, lots of pictures, everywhere, about everything

### Dependency injection (probably the hardest to grasp this week)
Problem: You have a bunch objects that need some configuration data (like methods for getting things out of your database, language information, connection information, and whatever else). Or maybe you have some objects designed to provied access to your data (providers) and you want to be able to sw 
First Solution: Just add a function to the class that updates the value when it is needed.
```javascript
	model.prototype = {
    	value: "starting",
    	updateVal: function(){
       		this.value = "new value that i got from database" 
        }
    }
```
While this *does* work you are going to have a mass of duplicated code, every object that need access to a database thing is going to have to write it's own update function and you are tightly coupling this object to your database/api/whereever. This is going to be hard to maintain.
Better Solution: Create a object that knows how to *inject* an update function into your object. We are going to use backbone demonstrate this becuase it takes quite a bit of bolierplate code to do. 
```javascript
	var ourModel = Backbone.Model.extend({
    
    }).inject({updater:databaseUpdater})
```



### Facade

### Observer

### Command

### Mediator

### Template
