# Orisa Bot Documentation and List of Commands

List of instructions and general information about Orisa. The code lives [here](https://github.com/bhavdeepsinghb/whoison)

[**What's New?**](#what's-new)

**Current Version:**

    beta - 1.1.0 (currently testing)

    stable - 1.0.10

## Getting Started

Orisa was initially created to notify team members about your online availablility. As such,  most of your interactions with Orisa will depend on your online status. 

Another thing to remember is that all of Orisa's commands start with an exclamation mark (`!`)

Make sure Orisa is online and type `!on`. If everything was set up correctly, the bot should have responded and set your status as online. 

You can check this by typing `!whoison`. This shows you a list of users who are also online along with the time they have been online for.

When you're done playing and want to turn your status to offline, type `!off`. 

In the most basic sense, you will be using these three commands the most, however, there are a lot of cool things Orisa can do you for you, the following is a table of contents for all Orisa commands divided by section

## Table Of Contents

* [**Basics**](#basics)
* [**Grouping**](#grouping)
* [**Practice**](#practice)
* [**Bug Reporting**](#bug-reporting)
* [**Misc**](#misc)

## Basics
****
## !help
    
    Gives you a link to this page

* **Arguments**
    
    _None_

* **Usage**
    
    _For All Users_

        > !help

        Hi, I'm Orisa, a bot made by Zoid to automate the boring stuff on this
        server. For a full list of commands and documentation follow the link below
        https://link-to-the-readme-page.html


    
## !status
    
    Check if the bot is online and processing instructions

* **Arguments**
    
    -v : verbose - returns the number of instructions processed and bugs reported so far

* **Usage**
    
    _For All Users_

        > !status

        The bot is online and has been running for 0:02:51

        > !status -v

        The bot is online and has been running for 0:02:51
        In this session, 
        3 unique instructions have been processed
        1 unique bugs have been reported
        


## !on
    Sets your status to online. 
    You can now form groups, be included in groups and will be considered for captaincy during practice.

* **Arguments**
    
    `@a_user` - set someone else's status as online (Admin ONLY)  

* **Usage**
    
    _For All Users_

        > !on

        Zoid is now online!

    _For Admin_
        
       > !on @SampleUser

        Admin command invoked by Zoid
        SampleUser is now online!

## !whoison
    Shows a list of all online players

* **Arguments**

    _None_

* **Usage**
    
    _For All Users_

        > !whoison

        Zoid has been on for 0:00:57
        SampleUser has been on for 0:00:21
        Bastion has been on for 0:00:03


## !off
    Sets your status to offline. 
    You are automatically removed from any groups and will not be considered for captaincy in practice.

* **Arguments**
    
    `@a_user` - set someone else's status to offline (Admin ONLY)

* **Usage**
    
    _For All Users_

        > !off

        Zoid is now offline

    _For Admin_
        
        > !off @SampleUser

        Admin command invoked by Zoid
        SampleUser is now offline!



## !allon
    (Admin ONLY) Sets all members' statuses to online

* **Arguments**
    
    _None_

* **Usage**
    
    _For Admin_
        
        > !allon

        Admin command invoked by Zoid, everyone is on!


## !alloff
    (Admin ONLY) Sets all members' statuses to offline and destroys any active groups

* **Arguments**
    
    _None_

* **Usage**
    
    _For Admin_
        
        > !alloff

        Admin command invoked by Zoid, everyone is off! All groups destroyed!

## Grouping
****

## !group {user/list of users}
    
    In order to use groups, please make sure you're online.
    If ungrouped - creates a new group of calling user + all valid mentioned users
    If grouped - adds all valid mentioned users to current group

* **User Validity**
    
    A user is consiered valid if they are online and not in any existing groups. Any users considered invalid have to be grouped up again.
    Other examples of invalidity include trying to group up with yourself, etc.

* **Arguments**
    
    (_Required_) User or list of users to group up with.

    Note - it is OPTIONAL to mention yourself when creating a group, but you need to mention at least one OTHER user.

* **Usage**
    
    _For All Users_

        > !group @SampleUser

        New Group Created for Zoid!
        The following players were added to the group ['SampleUser']

        > !group @anotherSampleUser
        
        The following players were added to the group ['anotherSampleUser']

        > !group @invalidUser

        The following players were not added since they are already grouped or
        offline, type !ungroup to remove yourself or !on to set your status 
        as online ['invalidUser']

## !whoisgrouped
    Shows a list of all active groups

* **Arguments**
    
    _None_

* **Usage**
    
    _For All Users_

        > !whoisgrouped

        The following is a list of all groups
        1) ['Zoid', 'SampleUser']
        2) ['Foo', 'Fighters', 'Bar']


## !ungroup
    If you were in a group, removes you.

    If there was just one other person in your group, they are ungrouped too and your group is destroyed.

* **Arguments**
    
    _None_

* **Usage**
    
    _For All Users_

        > !ungroup

        Zoid has been removed from the group

        > !ungroup 

        Zoid has been removed from the group
        Zoid's group has been destroyed, SampleUser has now been ungrouped

## !destroygroup {group number}
    (Admin ONLY) Destroys group with corresponding number

* **Arguments**
    
    (_Required_) A group number. 

    Group numbers are seen using the !whoisgrouped command

* **Usage**
    
    _For Admin_
        
        > !whoisgrouped

        The following is a list of all groups
        1) ['Dj_RealMeal', 'Ibonal (E-Bot)', 'z99ghostrider']
        2) ['Mac_Shizzle', 'Zoid']

        > !destroygroup 1

        Admin command invoked by Zoid
        Dj_RealMeal has been removed from the group
        Ibonal (E-Bot) has been removed from the group
        Ibonal (E-Bot)'s group has been destroyed, z99ghostrider has now been ungrouped



## Practice
****

## !practice {number of games} [list of arguments]
    (Admin Only) Creates a new practice session with unique maps and captains for each game. 

    Check out arguments to customize your practice

* **Notes**
    - At least 12 players must be online at the time practice is being created. If fewer players are online, a confirmation message is sent and the caller of the practice must react to it in within 60 seconds.
    - By default captains are unique for each game, but will be repeated if too few players are online
    - To be considered for captaincy, a user must be online (!on) before practice is invoked
    - When not using custom maps, the first map will be Control Point followed by Assault and Escort or Hybrid in that order. After the third game, this order switches around.

* **Arguments**
    
    *Required*

    * Number of games  - the number of games to be included in this practice

    *Optional*

    * `-num` - Maps may be repeated  
    * `-nuc` - Captains may be repeated
    * `-cm  <list of maps>` - Custom maps
        * List of maps is the name of all maps you wish to have
        * The name of a map is case insensitive and only needs one word. 
          
          King's Row = king's row = king's = king
        * If number of custom maps is less than the number of games in the practice, custom games will be played first and rest of the games will be randomized
* **Usage**
    

    _For Admin_
        
      > !practice 1

        Creating a practice session with 12 players where captains will be unique 
        and maps will be unique
        The number of games does not cover all game modes, you will start with 
        Control map
        Game 1: trippymcgee vs Ibonal (E-Bot)
        Map: Busan

      > !practice 4 -cm Busan Temple King's Route

        Creating a custom practice session with 10 players where captains will be unique
        Seems like less than 12 players are online, if you have enough randos or 
        those who aren't online, please react with :thumbsup: to proceed WITHIN 60 
        SECONDS
        
      > [Reacted]
        
        Game 1: Ibonal (E-Bot) vs Driller2012
        Map: Busan
        Game 2: BankerOfDoom vs Mac_Shizzle
        Map: Temple of Anubis
        Game 3: tristnieves9 vs Chicken Joe
        Map: King's Row
        Game 4: Dj_RealMeal vs trippymcgee
        Map: Route 66


## Bug Reporting
****

## !bug
    Minimal bug report, notifies @Zoid of a bug, marks the location in the run's logfile

* **Arguments**
    
    _None_

* **Usage**
    
    _For All Users_

        > !bug

        Bug Reported, thank you.
        Ping @Zoid for updates

## Misc
****

I made some commands for fun, these aren't logged and their bugs would take secondary priority. 

SOME commands will NOT use the exclamation mark (`!`)


## F 
    Lets the server know you have paid your respects.
    Case insensitive - f = F
* **Arguments**
    
    _None_

* **Usage**
    
    _For All Users_

        > f

        Zoid has put some respecc on it

## X / A
    Assemble either the X-men or the Avengers
    Case insensitive - x = X / a = A
* **Arguments**
    
    _None_

* **Usage**
    
    _For All Users_

        > a

        Zoid has assembled the Avengers!

        > X

        Zoid has assembled the X-Men!

## !{name}cute
    Returns a message about the cuteness of user with {name}

* **Arguments**
    
    (_Required_) name - this would be the na me of a person on the team
    * The name must be something you would call out during a game and not necessarily their discord name/nickname

* **Usage**
    
    _For All Users_

        > !zoidcute

        Zoid is no longer ugly

        > !ibcute

        Ibonal (E-Bot) was never ugly!

* **Hint** - try !pantscute

***

## What's New?

* **Introducing Docs!**

    Starting this version, all instructions, versions and updates will be documented! This instructions document was the first part of the process and will continue to be maintained as new instructions are added. With versioning, old versions of the bot will be archived to store depricated features. 

* **Version 1.1.0!**

    With the latest changes, Orisa enters its first notable update. 
    
    We've gone from being a small script called "whoison" to a full fledged multi function bot and it was time to act like an actual project by cleaning up and modularizing the code base. This was a start and will continue to be done in minor updates. 

    New features
    * [`!bug`](#bug) - reports a bug by pinging the developer and marking logfile location
    
    