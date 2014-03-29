coffeescript
============


1. Intro to Coffeescript

    -What is Coffeescript? 
    
        A programming language that transcompiles into JavaScript. Inspired by Ruby and Python.
            -Transcompiles means that you must compile your coffeescript into .js files

    -Why was it made? 
    
        It uses syntax that improves readablity as well as requires less written code. (~1/3-1/2 less).

    -What is it for? 
    
        Is used in frontend apps (including Angularjs).
        
        Is used in backend apps (especially Nodejs)(is included in ruby on rails)

    -Why use it over regular Javascript?
    
        -Less Code
        
        -Easier to Read
    
2. Cons of Coffeescript?
 
    -Adds an additional step of compiling.

    -the javascript that is produced isn't written by you, so it can be harder to read.
    
    -Troubleshooting can be a pain because you have to check between coffescriptfiles and javascript files.

4. Coffeescript set-up.
        

        1. Make sure you have node.js installed (this should already have been done in another class)
        
        2.  npm install -g coffee-script
        
        3. Test to see if you have coffee-script by typing coffee -h in terminal (should get a list of options)
        
        4. Make a new directory called coffee
        
        5. Create a new file in directoy called test.coffee

        6. Paste the following code in it....
        
        
        
                        initialData = [
                          { firstName: "Danny", lastName: "LaRusso", phones: [
                            { type: "Mobile", number: "(555) 121-2121" },
                            { type: "Home", number: "(555) 123-4567"}]
                          },
                          { firstName: "Sensei", lastName: "Miyagi", phones: [
                            { type: "Mobile", number: "(555) 444-2222" },
                            { type: "Home", number: "(555) 999-1212"}]
                          }
                        ]
                        
                        class ContactsModel
                          constructor: (contacts) ->
                            @contacts = ko.observableArray({
                            firstName: contact.firstName
                            lastName: contact.lastName
                            phones: ko.observableArray(contact.phones)
                            } for contact in contacts)
                        
                            @addContact = =>
                              @contacts.push
                                firstName: ""
                                lastName: ""
                                phones: ko.observableArray()
                        
                            @removeContact = (contact) =>
                              @contacts.remove(contact)
                        
                            @addPhone = (contact) =>
                              contact.phones.push
                                type: ""
                                number: ""
                        
                            @removePhone = (phone) =>
                              contact.phones.remove phone for contact in @contacts()
                        
                            @save = =>
                              @lastSavedJson JSON.stringify(ko.toJS(@contacts), null, 2)
                        
                            @lastSavedJson = ko.observable ""
                            
                            $ ->
                              ko.applyBindings(new ContactsModel(initialData))

        7. Examin the code you pasted... how does it differ from traditional Javascript?

        8. In your terminal make sure you are in the folder that contains test.coffee
        
        9. type the following                      coffee --watch --compile test.coffee       (the test.cofffee is the name of the file you want to have compiled)
      
      10. You will now have a new file created called test.js (this is your compied coffeescript.)
      11. Because we called "watch" on the file any changes that are saved in your coffeescript will automatically be             updated to your .js file.

      ** Additional info. If you want to watch an entire folder and update all the coffee files to .js then type the following in terminal                 coffee -c -o js --watch source    
      

3. Tutorial-
            http://coffeescript.carbonfive.com/

5. Angular and coffeescript   
          - Great article on how to write anglar/coffescript    http://alxhill.com/blog/articles/angular-coffeescript/
