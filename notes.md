#Getting Started

- code in /server runs only on server
- code in /client only runs on client 
- everything else runs on both
- files in /lib are loaded before everything else
- any main.* file is loaded after everything else
- Static assets (fonts,images,etc.) go into the /public directory

##Templates 

##Finding Files

Meteor is great at finding files. No matter where you put your code in the /client directory, Meteor will find it and compile it properly. This means you never need to manually write include paths for JavaScript or CSS files.
It also means you could very well put all your files in the same directory, or even all your code in the same file. But since Meteor will compile everything to a single minified file anyway, we'd rather keep things well-organized and use a cleaner file structure.

**Note taht the name = "postList" attribute of the template element.This is the name that will be used by Meteor to keep track of what template goes where. 



#Handlebars

- Meteor's templating system. 
- Three main parts
  - Partials
  - Expressions
  - Block Helpers

##Partials 
  - use the {{> templateName}}  syntax, and simply tell Meteor to replace the partial with the template of the same name ( in our case postItem).

##Expressions 
  - such as {{ title }} either call a property of the current object, or the return value of a template helper as defined in the current template's manager.

##Block Helpers
  - special tags that control the flow of the template, such as {{#each}}...{{/each}} or {{#if}}....{{/if}}


#Template Managers

 - Meteor keeps their templates and login seperated, and these templates dont do much by themselves.
 - In order to come to life a Template needs a **manager**.  You can think of the manager as the chef that takes the raw ingredients (your data) and prepares them, before handling out the finished dish to the water (the template) who then presents it to you. 
 - In other words, while the template's role is limited to displaying or looping over variables, the manager is the one who actually does the heavy lifting by assigning a value to each variable. 
- To keep things simple we will adpot the conventrion of naming the mangaer after the template except with a .js extension. 


#The Value of "this"
- JavaScript magic happening. 
  - The {{#each}} block helper not only iterates over our array, it also **sets the value of 'this' inside the block to the iterated object **
  -this.url can now return the current posts' URL.
  -the 'a' anchor element has a special hostname property to get back the link's domain name without the rest of the URL. 

##Find and Fetch 
  - In meteor find() returns a cursor, which is a reactive data source.  When we want to log its contents, we can then use fetch() on that cursor to transform it into an array. 

  -Within an app Meteor is smart enough to know how to iterate over cursors without having to explicityly convert them into arrays first.  This is why you wont see fetch() that often in an actual Meteor app. 

#Connecting Collections: Publications and Subscriptions

- So far we have had the autopublish package enabled which is not inteded for production applications.  As its name indicates this package simply says taht each collection should be shared in its entirety to each connected client.  This isnt what we want.


#Publications and Subscriptions
- Hard to wrap your head around. 

-This has led to a lot of misunderstandings, one being that Meteor is not secure. 

#The /lib folder
- Anything you put inside the lib folder is guranteed to load first before anything else. this makes it a great place to put any helper code that needs to be available at all times

#Named Routes




