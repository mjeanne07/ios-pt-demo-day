# iOSPT Demo Day

## Requirements

1. Fork and clone the repository
2. **Add your presentation content**
    1. Slide deck (4 required slides)
    2. Links
    3. Answer all questions 
    4. YouTube demo video (1-2 min max)
3. Polish your Github Code repository
    1. Add screenshots and an overview to your GitHub Code Repository
    2. You should make that repository the "Public Portfolio" for your project
    3. Look at [John Sundell's Splash project](https://github.com/JohnSundell/Splash) for inspiration (code, images, GIFs)
4. Create a pull request (PR) and **tag your TL and Instructor**

## Links

* Github Code: https://github.com/mjeanne07/Build-Week-Group-Lunch-Coordinator 
* Github Proposal: https://github.com/mjeanne07/ios-build-sprint-project-proposal
* Trello/Github Project Kanban: https://github.com/mjeanne07/Build-Week-Group-Lunch-Coordinator/projects/1
* Test Flight Signup (Recommended): https://testflight.apple.com/join/uHYmKSEz
* YouTube demo video (Recommended): https://youtu.be/jo6rAykw0Lo 
* Slides: https://docs.google.com/presentation/d/1Fy2EyEAtxhMvcBivtl7FKOc-NDLT0zNFXzB8JvOJMHA/edit#slide=id.g59aed71b69_1_238


## Hero Image

`<Post one screenshot in an iPhone Simulator frame or an iPhone 11 Pro render using placeit.com>`

## Questions (Answer indented below)

1. What was your favorite feature to implement? Why?

The feature to see a detail view of a restaurant before selecting it.  Before selecting a locatiion to eat, it seems natural to want to know more about the restaurant (address/cuisine) before making a decision.  The detail view also allowed more creativity to create custom views of the restaurant, i.e., with their logo. 

2. What was your #1 obstacle or bug that you fixed? How did you fix it?

The biggest obstacle for creating this app was solving the mystery of how the "user" variable was being updated when selecting a restaurant.  We tried multiple solutions, one was using a delegate to try to pass information, but ultimately used a segue and changed our user.swift file to be a 'class' insead of a 'struct'.  With the struct, we were making changes to a copy of the user and not our original array of users.
  
3. Share a chunk of code (or file) you're proud of and explain why.
        
    The Following code is in our User Controller swift file, which is basically the brain of our app.  This follows the creation, update, and deletion of our users and is critical for our app to function.

        func createUser(withUserName userName: String) {
           let newUser = User(userName: userName)
           
           users.append(newUser)
           self.signedInUser = newUser
           saveToPersistentStore()
       }
       
       func updateSelection(user: User, withRestaurantSelection restaurantSelection: String) {
           guard let index = users.firstIndex(of: user) else { return }
           
           var scratch = user
           scratch.restaurantSelection = restaurantSelection
           users.remove(at: index)
           users.insert(scratch, at: index)
           saveToPersistentStore()
       }
       
       func updateLunchTime(for theUser: User) {
           guard let index = users.firstIndex(of: theUser) else {return}
           users[index].lunchTime = !users[index].lunchTime
           saveToPersistentStore()
       }
       
       var earlyUsers: [User] {
           return users.filter({ $0.lunchTime == false })
       }
       
       var lateUsers: [User] {
           return users.filter({ $0.lunchTime })
       }
       
       func delete(user: User) {
           guard let index = users.firstIndex(of: user) else { return }
           
           users.remove(at: index)
           
           saveToPersistentStore()
       }
  
4. What is your elevator pitch? (30 second description your Grandma or a 5-year old would understand)

Hungry Homies is an app that allows users, such as cowokers in an office, to sign up and choose a location/ time to eat lunch.  The app allows user to choose between early and late lunch as well as their preffered lunch location.  The app also allows users to research their options, users can click on the detail view of all of the restaurants to learn more about what each restaurant offers, where its located, and how to contact the restaurant for further information.  Once the user selects a restaurant, they will receive a notification of where they are going and when to leave.    
  
5. What is your #1 feature?

The #1 feature would be restaurant selection, creating an easy way for users to decide on a location to eat. 
  
6. What are you future goals?

Future goals would be to incorporate more restaurant details related to daily discounts/ deals to let users to make better monetary decisions on where they eat lunch everyday.  

## Required Slides (Add your Keynote to your PR)

1. App Name / Team Slide
2. Elevator Pitch
3. Your #1 Feature (Customer facing — what can I do with your app?)
4. Future Goals

## Slide Requirements

1. 50 pt font minimum
2. Be concise — don't write sentences/paragraphs (put these in your slide notes for speaking)
3. 3-6 bullets maximum per slide
4. Do the squint test (can you read the text if you squint, if so, make the font bigger)
6. Images are always welcome
7. Do the Grandma Test (Would your Grandma understand you?)

### Optional Slides

1. Blooper: What's a funny bug or blooper? (screenshots/GIFs please)
2. Revenue Model: If the app was your sole source of income, how would you monetize it?

## Presentation Format

**7 minutes/team**

* 4 minute presentation (5 minute hard cap)
* 3 minutes of questions

We have ~12 teams presenting today — please practice your presentation with a timer (as a team), and make sure you fit within the time limit.

Plan on having one person present the slides and live demo. Please practice your presentation in front of a mirror or with your team 2-5 times. Have the app running and visible (Simulator or QuickTime) so you can quickly transition between slides and live demo.

* App Name / Team Slide (30 seconds)
* Elevator Pitch Slide (30 seconds)
* Your #1 Feature (30 seconds)
* Live Demo (2 minutes)
* Future Goals (30 seconds)
* Questions (3 minutes)
