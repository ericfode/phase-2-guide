## Eric's frount-end jargon cheat sheet

Responsive:
Responsive can refer to a few things depending on context:
- That the interface responds quickly and smoothly to user interaction.
- That the UI seamlessly scales and changes to fit smaller devices, this is progressively being done in just CSS. A good example of this is [Bootstrap](http://getbootstrap.com/ "Bootstrap"). Check it out on your phone and your computer, notice that thing moved around. All of this was done fairly seamlessly using just css.

Endpoint:
A Url that can be requested from a web server, most of the time this is API.

Asynchronously:
Remebering that computers tend to do things one step at a time we notice that there are cases when this could cause problems. For example, when you are making a request to a endpoint you don't want to hold up your whole UI waiting for the response to come back. This is solved by having the computer send off the requsted then instead of giving you back a value, you pass it a callback to execute when it is done. 

Callback function:
A function that you pass to another function (check out the code example below) to be executed when the first function is done.

```ruby
#this is a synchroness function
#every step happens in order, one at a time
#but slowthing will make the rest of the program wait until
#it's done doing it's thing
def slowthing()
	sleep(500)
    "Really long request"
end

#this is async using
#the function is called and it starts doing its work
#then when it's done it calls the function that you passed to it
#and does what ever you need done with that value
def slow_async_thing(&block)
	#Thread.new allows you to start a new "thread" of execution
    #In ruby this can be a precrious thing so don't do it unless you know why
    #you are doing it
    Thread.new do
    	sleep(500)
        #block is a function that was passed into this function
        #It is what ever work needs to be done with the data created by the function
        block.call("Really long request")
    end
end

def slowcall()
	x = slowthing
    puts x
end

#notice that this function does not assign any varibles
#instead it gives slow_async_thing instructions as to what to do with
#the generated data
def fastcall()
	#everything after the do is called a callback
	slow_async_thing do | val |
    	puts val
    end
 end
 
 slowcall()
 fastcall()
```

Scope:
- An area to put things

Out of Scope:
- When used refering to an idea it means that the idea is not part of the intent of the project. For example, you are talking about building a house and someone start talking about where the house should be located. While the location of the house is important it is *out of scope* for this conversation becuase it has little to do with the actuall house.
- When a computer tells you somthing is out of scope it means that it can not get access to it
```ruby
def scopefun
    #declaring x in the scope of the function
	x = 20
end
#x is not in the global scope 
puts x
```


