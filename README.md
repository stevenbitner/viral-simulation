# Virus

## Project Outcomes:
Develop a Java program that uses:
- A Graphical User Interface (GUI)
- Random numbers
- Periodic updates using a Timer
- Event-driven programming

## Preparatory Readings:
- ZyBooks chapters 1-13
- Java Documentation
	- Random: https://docs.oracle.com/javase/8/docs/api/java/util/Random.html
	- Timer: https://docs.oracle.com/javase/7/docs/api/java/util/Timer.html
	- Swing/AWT features as needed

## Background Information:
### Project overview:
The Covid-19 virus is dominating every single one of our lives at the moment and needs no introduction.
New terms such as social-distancing are now fully ubiquitous in our everyday language.
Current recommendations are that people not get within six feet of each other.
Clearly this is a sudden, and drastic, change for virtually every human on the planet.
Some people are going a bit too far.

<img alt="People in plastic bubbles" src="https://res.cloudinary.com/dm3fdmzec/image/upload/v1585692716/giphy_at3z5n.gif" width=500 />

While others are as-yet unwilling to change their habits from the status quo.

<img alt="Spring breakers spreading the love...and the virus" src="https://res.cloudinary.com/dm3fdmzec/image/upload/v1585692580/85_ftvwcb.jpg" width=500 />

### Project Requirements:
Your application must function as described below:
1. A graphical interface component must be present to allow a user of the application to update the percentage of the population complying with social distancing recommendations.
	1. Changes to the value should be reflected in the graphical simulation.
1. A display of color spots shall indicate the status of members of the population.
Green for healthy, red for infected and black for deceased.
Optionally, add some additional indicator for non-compliant persons.
In the [demo below](#demo-of-completed-program), an orange outline is used.
1. The program must run in time steps indicating the effects of social distancing on the spread of infectious diseases such as the Coronavirus.
	1. In each time step, every _person_ (cell in the grid) should be analyzed and displayed according to their status.
	1. If the person has not yet been exposed to the virus, there is a 75% possibility that they will contract the virus if they come into contact with an infected person.
		1. Coming into contact means that one of the two people involved is not complying with social distancing guidelines.
	1. After four time steps an infected person should stop being contagious. The probability of death should be set as 3%. The other 97% go back to a healthy state but will no longer be vectors for the spread of the virus. This means that they will remain green for the remainder of the program run and will not transmit the virus.
	1. Choose 5% of the initial population at random to be infected.


#### Demo of Completed Program
![Demo of running virus program](https://res.cloudinary.com/dm3fdmzec/image/upload/v1585693265/virus-demo_qembfd.gif)

### Implementation Notes:
1. Create a project that is object oriented, therefore there should be several classes.
1. A Timer can be used to trigger an action to occur every _**X**_ milliseconds. For example:
	```java
	// Infector is a class that you need to define, which implements the ActionListener interface
	ActionListener infect = frame.new Infector(); // Infector is an inner class of the `frame` object
	// STEP_TIME, below, is the number of milliseconds between updates
	Timer t = new Timer(STEP_TIME, infect);
	// start the Timer. It will repeat every STEP_TIME milliseconds until stopped 
	t.start();
	```
1. `repaint()` is needed inside a JComponent to re-draw the display after updating the data.
1. All of the % probabilities can be implemented using a `Random` object. Simply create a `new Random()` instance at the start of your program and any time you need to check against `THRESHOLD` %. For example, if the fatality rate is 3%, you can determine if a person dies by running something like:
	```java
	// start of application
	Random percentageChecker = new Random();
	// ... someplace else, during timestep checks
	// assume FATALITY_RATE is an integer set to 3
	boolean deceased = percentageChecker.nextInt(100) < FATALITY_RATE;
	// take action
	```

### Submission Requirements:
1. All code must be added and committed to your local git repository.
1. All code must be pushed to the GitHub repository created when you "accepted" the assignment.
	1. After pushing, with `git push origin main`, visit the web URL of your repository to verify that your code is there.
	If you don't see the code there, then we can't see it either.
1. If your program will not compile, the graders will not be responsible for trying to test it.

## Important Notes:
* Projects will be graded on whether they correctly solve the problem, and whether they adhere to good programming practices.
* Projects must be received by the time specified on the due date. Projects received after that time will get a grade of zero.
* Please review the academic honesty policy.
	* Note that viewing another student's solution, whether in whole or in part, is considered academic dishonesty.
	* Also note that submitting code obtained through the Internet or other sources, whether in whole or in part, is considered academic dishonesty.
	* All programs submitted will be reviewed for evidence of academic dishonesty, and all violations will be handled accordingly.
