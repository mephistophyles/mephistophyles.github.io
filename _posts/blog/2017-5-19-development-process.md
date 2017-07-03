---
layout: post
title: Development Process for Small Projects
blog_group: blog
---

As someone who makes a lot of 'quick' projects in python, and talking to plenty of friends who do the same, I've noticed there are generally two ways I approach the projects with different pros/cons. In order to elaborate and for my own edification, I have a similar project built using the two approches on my github [here,](https://github.com/mephistophyles/predator_prey) that helped me better realize each approach's relative utility and pitfalls. The approach is two approaches to a predator-prey simulation that scales. The Lotka-Volterra equations are interesting, especially the competitive version, but they are analytical solutions to a very specific set of beginning conditions. While they are useful in their own respect, I would prefer to play with the animal behavior and discover any emergent behavior from these behavioral heuristics.

The first way a lot of projects get started is to dive right in.  Either by taking someone else's code as example or just setting something up. The ease with which python allows you to skip almost all boiler plate code and the plethora of libraries easily available through the PIP tool makes this the instinctive thing to do. The quick gratification of the work-reward feedback loop when you see the first output makes it an easy way to keep working on a problem. This is a great way to quickly get your hands dirty and iteratively build up something nice.

The second method is to not dive right in, but to take a step back. Think about what you want to make, take a holistic approach to each aspect of it (what classes do you need, functionality, what libraries do you know could work vs what libraries are out there for this, etc). This often leads to a broader information base, a better initial approach and cleaner code. The potential pitfall is that sometimes you will overthink a problem and can get stuck in an infinite loop of improving your design before you ever write your first line of code. Another possible downside is that if the project is small you can get demotivated for it and decide to abandon it before you 'finish' it. Over the course of a few months and several smaller projects this could theoretically be the difference between adding some interesting nuggets of knowledge to your toolbox and not.

### Approach 1

I use NumPy a lot in my day job, so it was the first approach I thought up and so I decided to start with creating a world (in this case a simple grid) and randomly populating it with grass or food. The L-V equations assume food is unlimited and ubiquitous, but that's not always the case in real life and I wanted the flexibility to play with that variable too. Version 1 shows exactly that. In less than 50 lines of code I have a 100x100 board, with 100 pieces of 'food', but also 50 herbivores and 10 predators (in reality a NumPy 2D array with zeros as empty, ones for food, twos for herbivores and threes for predators). I also wrote it in such a way that I felt comfortable I could easily expand the functionality. The plan was to have the numbers in the array be a symbolic representation of the world, but to not store the data types in the array directly. A separate list of creatures would be iterated through on each time step to update states and movements, and then we repopulate the board before visualizing it.

Feeling happy with my approach so far I copy-pasted my code into a new file so I could iterate over it and add functionality (leaving the old on behind so I can easily check the progress). I created a Creature class, with functionality for eating, dying and moving. I also added a status function that quickly printed the current amounts of food and creatures of each level (the reasoning behind the levels was I wanted to have food chains that weren't a simply "a eats b, eats c, etc" I wanted possibly larger animals that could eat at different levels of the food chain, but also large animals that were too big to eat). 

|---|---|
|![Image of the v2.0 of first approach]({{site.url}}/images/pred_prey/single_pred_prey2.png) |![Image of the v3.0 of first approach]({{site.url}}/images/pred_prey/single_pred_prey3.png)|
|---|---|
|First attempt at visualizing predator-prey | Showing statistics with the visualization|

This worked nicely, but didn't visualize well in a continuous fashion. Showing the plots/status was blocking the program from running further. So, building on my knowledge of NumPy and Matplotlib, I changed my plot into an interactive one, expanded the creature class a bit, printed the state of the animation both to console and the plot, and finally saved my output to a text file. This meant after a bit of tweaking I could run my simulation with any desired parameters (and as many times as I want, Monte Carlo anyone?) and have the output saved in a text file for later processing. This allowed me to play around with the parameters and see how close my simulations could come to the LV equations.

### Approach 2

As I stated above, the second approach involves a bit of searching around and thinking before you actually start to build anything. In my case I came across pygame, which is a module that is used for building (surprise) games. This suits my needs because not only do I want a controlled eventloop, but I also want to have efficient handling of visualization. I had come across a number of other options along the way, other peoples' simulations on github or blogs similar to mine, but nothing I felt I wanted to 'borrow' to build on. I did use Peter Collingridge's [site](http://www.petercollingridge.co.uk) as a guide to get the pygame visualization, in this case just some OpenGL primitives, aspects working. Using what I also learned from approach 1 (I know, cheating), I built another creature class and another world class. Each with a built-in display functionality.

|---|
|![Pygame initial showing]({{site.url}}/images/pred_prey/pygame1.png)|
|---|
|Visualization within PyGame|

The expanded functionality let me build a cleaner looking interface, with a smoother graphics display. It also allowed me to play around with pygame, which I thought was cool. I do also have some small fixes I intend to make, before I consider the project a success and move onto the data analysis phase. At that point I will write up a project post about it.

### Conclusion

As in many cases, there is no 'right' approach. The approach I would advocate definitely depends on the situation. If you want to get a quick idea of something simple, then quickly hacking something together is the way to go. As a rule of thumb, iff it is something that you won't end up finishing in one session I would highly recommend the second approach. Nothing is more frustrating than dealing with hastily written code that wasn't fully thought through (doubly so if it's your own code).

Personally I would like to try a blended approach, since I am always motivated by visible results. Once you have something working, you can always take a step back and approach the problem with a bit of experience (which brings with it the joy of self-discovery) and properly design a solution. I find that the investment of time and effort into getting your hands dirty with a solution (even if you end up totally throwing it out) is worth it. 

An additional help with the current approach, is that if you change the heuristics, you can interpret the data differently. For example if you make the food a lot more scarce, add some obstacles and change the predator behavior you could potentially have a zombie survival simulator. Expanding the behavior of the creatures is fairly trivial because I kept adding new behaviors and had specific usecases in mind during the design process.

I also wanted to have a repository online where I could point people to a partially worked-out example of the iterative process of building something. Even in programming the largest journey starts with the smaller steps.