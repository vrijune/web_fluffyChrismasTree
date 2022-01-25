Web Lab 06 &ndash; Advanced CSS & Intro to JavaScript
==========

Begin by forking this repository into your namespace by clicking the ```fork``` button above, then selecting your username from the resulting window. Once completed, click the ```clone``` button, copy the ```Clone with HTTPS``` value. Open IntelliJ, and from the welcome screen click ```Check out from Version Control -> Git```, then paste the copied URL into the ```URL``` field of the resulting window. Provide your GitLab username and password if prompted.

Explore the files in the project, familiarizing yourself with the content.

When complete, demonstrate your code to your tutor. This must be verified with your tutor by the end of the week.

Exercise One
----------

Remember the Christmas tree from lab four?

![](./spec/ex01-screenshot.png)

In this exercise, you'll re-implement Exercise Two of that lab, where you made the baubles expand when hovering over them with the mouse. However, this time, set the *scale* function of the baubles' ```transform``` property, rather than directly changing the baubles' width or height.

Once you've done that, further modify your code such that the bauble moves smoothly between "small" and "large" states. Decide whether it would make sense to use a *transition* or an *animation* for this exercise.


Exercise Two
----------

Make a copy of the files in the ```ictgradschool/web/lab06/ex01``` folder and place them in the ```ictgradschool/web/lab06/ex02``` folder. You may need to create this folder yourself. Close all open editor tabs, then when opening files to edit, open them from the ex02 folder.

Open the ```christmas_tree.html``` file from the ex02 directory of the project. Use CSS ```@keyframes``` animation to get the baubles to all fall down simultaneously and bounce up and down twice before coming to a standstill. Get the animation to restart each time you hover over the image. The baubles should remain on the ground after the animation is complete.

##### NOTE:
*All* baubles should animate *at the same time*, whenever you hover over any part of the image. They shouldn't animate individually.

##### HINTS:
- Think about how you'd style all your ```.bauble``` elements to include your animation, but only when you're hovering over the ```#container```.
- Have a look at the ```animation-fill-mode``` property to make the baubles stay on the ground.
- Do you need to set the baubles' initial positions in the ```@keyframes```? What happens if you leave the ```from { }``` section blank?

### (Bonus) Exercise 2.5
As an extension to exercise two, make the baubles stay on the ground at all times when not animating, even when you're not hovering over the image. You should be able to add this functionality with only **one** extra CSS rule, and *without* modifying any of the CSS already written.


Exercise Three
----------

In this exercise, we'd like to modify our Christmas tree so that, rather than all baubles dropping together when hovering over the image, each bauble drops *individually* when you *click on* that bauble with the mouse.

While CSS animations are very powerful and can accomplish a lot by themselves, we can't respond to mouse clicks within our CSS. For that, we'll need to use JavaScript.

Take note of the files located in the ```ictgradschool/web/lab06/ex03``` directory. Begin by copying your ```@keyframes``` animation you developed for exercise two into ```style.css```, and modifying the selector for the ```.animated``` class to apply those animation keyframes, and to have the animated elements stay on the ground after the animation is complete - just as you did in the previous exercise.

Now, we'll add some JavaScript code which will add the ```.animated``` class to each bauble when clicked. To do so, follow these steps:

1. Create a new JavaScript file in the ex03 directory. Call it ```baubledrop.js```.
2. Add a ```<script>``` tag to the ```<head>``` of ```christmas_tree.html``` which points to ```baubledrop.js```.
3. Add a *function* definition to the JS file. Make the function take a single *argument* (parameter), and log it to the console for testing purposes. For example:

    ```js
    function dropBauble(baubleId) {
        console.log(baubleId);
    }
    ```

4. In ```christmas_tree.html```, make each of your bauble images *call* your function when clicked, passing in its own id as an argument. You may do this by setting that element's ```onclick``` property, like so:

    ```html
    <img id="red" class="bauble" ... onclick="dropBauble('red');"/>
    ```
    
    Once this is done, you'll be able to click each of the baubles and have their ids displayed in the browser console when clicked (see [here](https://developers.google.com/web/tools/chrome-devtools/console/) for Chrome, [here](https://developer.mozilla.org/en-US/docs/Tools/Browser_Console) for Firefox).
    
    **NOTES**:
    - There are multiple ways of event handling in JavaScript, and this is *just one* of them. You'll learn about others later :)
    - Rather than *hardcode* the id of the bauble in the function argument as shown above (e.g. ```dropBauble('red')```), you can directly supply the element's id itself, using ```this.id```.
    
5. Write code in your function so that the ```animated``` class is applied to a bauble when it is clicked. The ```document.getElementById()``` function, and the ```classList``` property, should help with this as shown in the lecture slides.

### (Bonus) Exercise 3.5
As an extension to exercise three, further modify your code so that if you click on a bauble that's already animating (or has finished animating), its animation will stop and it will return to its original position.


Exercise Four
----------

In the ```ictgradschool/web/lab06/ex04/exercise04.html``` file, you will find three Scalable Vector Graphics (SVG) elements embedded in the page. These represent a maze, a figure and a monster. Using CSS animations, animate the monster chasing the figure through the maze. You should ensure that:
- Neither the figure nor the monster pass through any of the maze walls
- The figure and the monster use different ```@keyframes``` for their animations
- The monster gives the figure a slight head start
- The monster should almost, but not quite, catch the figure at the end of the maze
