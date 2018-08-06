---
layout: post
title:      "My NBA Basketball Simulator CLI Project"
date:       2018-08-06 19:24:04 -0400
permalink:  my_nba_basketball_simulator_cli_project
---


Hello everyone! This is the first of my portfolio projects here at Flatiron School. When proposed with the opportunity of creating a project, I had to think of things that really interested me. I'm a big basketball fan, which made me think that it'd be really cool to create a CLI project that scarped a website fo knowledge on NBA players. I decided to use https://www.basketball-reference.com as the website I would scrape. 

So, I have my idea, but where do I go from there?  I've never used an ide outside of the Learn IDE, which wasn't cooperating with me at the time.  I decided to go with Microsoft Visual Studio Code, with a little help of googling "What's the best IDE". Setting up the IDE was a little confusing, but soon enough I was ready code...except I've never started a project from scratch before.  What do I do?  Thankfully, Avi had his Building a CLI Gem video that was very helpful.  In this video, it layed out a general outline of how to begin/build my project.  The steps I got from it were:  Discover how you want your project to look, build project with fake data, figure out what selectors to use, replace fake data with real data, find out why your code is breaking, finish project.  I'll be going over my experience in each of these steps during this project, and discuss some steps I didn't expect to be there.

### Look

The first thing I wanted to take into account when planning this project was what the user would see.  I felt as though it was important to make sure that whatever information was presented to the user was understandable at first glance.  I wanted to limit any confusion that the user may have when first loading up the project.  This was what I ultimately come up with in regards to how I wanted my Basketball Simulator to look:

```

"Hello, this is the basketball-simulator using https://www.basketball-reference.com/ to help you with all of your basketball needs!  Are you looking for:

1. A specific player from the 2017-2018 NBA season?
2. Or would you like to play our basketball game?

```

Let's say that the user wants to check up on their favorite player, Kristaps Porzingis.  They would enter 1, which would lead to this:

```

"What player would you like to see?"

```

The user types in Kristaps Porzingis, and should see this:

```
Name: Kristaps Porzingis
Height: 7-3
Weight: 240lb
Team: NYK
Birthday: 1995-08-02
Birthplace: Latvia
Points per Game: 22.7
Total Rebounds per Game: 6.6
Offensive Rebounds per Game: 1.3
Defensive Rebounds per Game: 5.3
Assists per Game: 1.2
Steals per game: 0.8
Blocks per Game: 2.4
Field Goal %: .439
3 Point %: .395
Free Throw %: .793

Thank you for using this application today. Would you like to go again? Y/N?

```

Okay! That's good!  This is a pretty decent way to present the data that I want to give to the users.  Of course there are several "responses" if there is a user-input issue (like putting an invalid name, or entering "cupcakes" when asked what you wanted from the simulator), but those are simple enough responses so we can skip describing that in this post.

## Building project using fake data

So, the purpose of this step is to assemble/code my gem so that it is functional before scraping the information from sites. It's important to do this so that funtional progress can be seen. Also, it's easier to break things down this way so I won't be worried about too many aspects of the project at once. Focus on one thing at a time, and that will make things exponentially easier.

Cool, so knowing that I want fake data, that means that I should choose two players from the NBA. I chose Russell Westbrook and Kevin Durant. So, if I stub out that fake data, what the program should look like is this:

```

Name: Russell Westbrook
Height: 6-3
Weight: 200lb
Team: OKC
Birthday: 1988-11-12
Birthplace: California
Points per Game: 25.4
Total Rebounds per Game: 10.1
Offensive Rebounds per Game: 1.9
Defensive Rebounds per Game: 8.2
Assists per Game: 10.3
Steals per game: 1.8
Blocks per Game: 0.3
Field Goal %: .449
3 Point %: .298
Free Throw %: .737

Thank you for using this application today. Would you like to go again? Y/N?

y

"Hello, this is the basketball-simulator using https://www.basketball-reference.com/ to help you with all of your basketball needs!  Are you looking for:

1. A specific player from the 2017-2018 NBA season?
2. Or would you like to play our basketball game?

1

"What player would you like to see?"

Kevin Durant

Name: Kevin Durant
Height: 6-9
Weight: 240lb
Team: GSW
Birthday: 1988-09-29
Birthplace: District of Columbia
Points per Game: 26.4
Total Rebounds per Game: 6.8
Offensive Rebounds per Game: 0.5
Defensive Rebounds per Game: 6.4
Assists per Game: 5.4
Steals per game: 0.7
Blocks per Game: 1.8
Field Goal %: .516
3 Point %: .419
Free Throw %: .889

Thank you for using this application today. Would you like to go again? Y/N?

n

Thanks again, have a great day!

```


This part wasn't too difficult, because all I really had to do was create the "menu", or the interface that the user will be interacting with.  This took me maybe an hour or two, not necesarily because it was difficult, but because I was getting use to using an environment other than Learn IDE.  Here's the code I made for this:

```

class BasketballSimulator::CLI

    def call
        greeting
        choice
    end

    def greeting
        puts "Hello, this is the basketball-simulator using https://www.basketball-reference.com/ to help you with all of your basketball needs! Type exit if you want to quit." 
    end

    def choice
        input = nil
        puts "Are you looking for:",
        "1. A specific player from the 2017-2018 NBA season?",  
        "2. Or would you like to play our basketball game?"
        input = gets.strip.downcase
        if input.to_i == 1
            single_player
            goodbye
        elsif input.to_i == 2
            game
            goodbye
        elsif input == "exit"
            goodbye
        else
            puts "Please select either 1 or 2 or exit."
            choice
        end
    end

    def single_player
        input = nil
        input2 = nil
        @players = BasketballSimulator::Player.allplayers
        puts "What player would you like to see? Please be very accurate with spelling and hiphens, etc."
        input = gets.strip.downcase
        @players.each do |player|
            if player.name.downcase == input
                break if player.name.downcase != input 
                puts "Name: #{player.name}", "Height and Weight: #{player.height_and_weight}", "Team: #{player.team}", "Birthday/Birthplace: #{player.birthday_birthplace}", "Points per Game: #{player.points}", "Rebounds per Game: #{player.rebounds}", "Assists per Game: #{player.assists}", "Steals per Game: #{player.steals}", "Blocks per Game: #{player.blocks}", "Field Goal %: #{player.fg}", "3 Point %: #{player.threept}", "Free Throw %: #{player.ft}"
            end
        end
        if input == "exit"
            goodbye
        else
            puts "I don't quite understand, let me try again."
            single_player
        end
    end

    def game
        puts "Please enter 5 player names"
        puts "Please enter another 5 names"
    end

    def goodbye
        puts "Thank you for using this application today. Would you like to go again? Y/N?"
        input = gets.strip.downcase
        if input == "y"
            call
        elsif input == "n"
            puts "Thanks again, have a great day!"
        else 
            puts "What did you say? Please be very specific in spelling."
            goodbye
        end
    end

end


```

I ran this, and my program shot out stats for Russell Westbrook and Kevin Durant when I input either of their names. Success! That sense of accomplishment, even if it wasn't a necessarily difficult task, was still enough to help push me to continue with the rest of the project.  Okay!  Onward to the actual scraping part!

## Scraping/Finding Selectors/Mental Breakdown

Okay, so this is where everything got a little bit more difficult.  This was very different than all the scraping labs that we've done before, primarily because the elements that I had been used to selecting were simple css elements. When I inspected basketball-reference's website, I saw a bunch of elements that I didn't recognize.  This is why stack overflow exists!  I looked up these elements, and discovered that they were HTML5 data attributes.  This was really interesting, because this was something I hadn't dealt with before.  However, this initial intrigue was quickly replaced with anguish. I played around with the elements a lot, and eventually got through my first level of scraping, which was me scraping every player's link to their respective profile page. This wasn't too difficult, although I found out the hard way that I can't produce the text between "< a href >" anchor points.  So, this means that I couldn't assign the players their actual name yet, so I found the next best thing which was a "Last Name, First Name" formatted text.  This is my "allplayersnames" method in the scraper class:

```
def self.allplayers
        players = []
        doc = Nokogiri::HTML(open("https://www.basketball-reference.com/leagues/NBA_2018_per_game.html"))

        doc.css('.left[data-stat="player"]').each do |reverse_names|
            player = self.new
            player.selector_name = reverse_names['csk']
            players << player
        end
        players
end
```

What this method does is stores all the players' "reverse names" into an array, which will be necessary to collect each player's respective link.

The allplayer_links method I created then iterated through this array of reverse names of the players and grabs the portion of the link that's provided.  It then appends that link portion onto the base url of the website.  Both of these methods were pretty simple as soon as I got used to selecting the data-attributes that this website used.  The problem was the next method, which applied all the respective individual stats to each instance of the player object.  The way that I typically code is just throw in some code, and test it, which normally would be fine.  However, this is when I first discovered a dreaded issue: the sheer amount of things that I'm scraping. 

Unlike the couple of deals that Avi scraped on his website, or the two players in the array that I used for my fake data, the actual NBA has hundreds of players.  NBA teams can have an active roster of 12 players, and typically are allowed three players on reserve.  This means that there are typically 15 players on each NBA roster.  With 30 teams in the NBA, that means that the amount of players that need to be scraped would be 450.  That's a lot of scraping that needs to be done.  My normal development time for any project is already probably 2 hours (of actual working time).  However, each time I test my program to see if I am selecting the correct element, it scrapes through all of these players and their links, which took on average 8-10 minutes each time I ran it.  There were times that I was glad to see that my code broke, because that meant that I didn't have to wait 8-10 minutes just find out that the player's points stat was empty.

Trying to figure out what elements to select was already difficult, especially considering I wasn't too used to the HTML5 elements, and having my runtime being 8-10 minutes long didn't help the situation out.  Despite all this, I finished my project, with the caveat that I put my game portion of it on hold.  

## Reviewing my code
So, my project is done!  Or so that's what I thought when I ran it.  It wasn't until now, as I am writing this blog, where I discovered something was off.  As it was originally written, the program would run as it normally would, but if you wanted to search up another player, it would call the program all over again.  The problem with that is that the way I wrote it had it rescraping the two levels of the website and create all these instances of the player object each time that the call method was run.  To resolve this, I created two call methods, one which was the initial call that created the array of instances of players, and the other being a call that didn't do that.  Once I did that, I added a few spaces throughout the program so everything was more legible.

## Takeaway

This was definitely a trying time, but also a time where I discovered more about myself.  There were many times where I'd want to just quit programming altogether.  This was already my second time attempting to study software engineering, and now it's come once again to defeat me.  It was that thought that kept me going.  I would not be defeated again by this.  And I wasn't, and you won't be too.  Keep going, keep pushing, and keep coding.

If you'd like to look at my repo for this, you can find it here: https://github.com/JTSarvida/Basketball-Simulator-Cli-Project-Attempt-2

Thank you again for reading this.




