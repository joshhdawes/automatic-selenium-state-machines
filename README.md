# A Tool for Automatic Generation of Selenium State Machines

Selenium is extremely powerful, but it's been recognised that manually coding interactions with the browser is a bit difficult.  This code becomes repetitive and a mental model of how it describes interactions can be difficult to build up.

Over the years, on the front of reducing the code-writing effort, some tools have emerged that enable you to record your interactions with the browser and generate selenium testing code.  These tools are great, but *machine-generated* selenium code can be even harder to understand than manually-written code.

So, in an attempt to make the situation a bit easier, we introduce a library for Flask-based applications that, with two lines added to your code base, eases the interaction coding process.  All you have to do is write your assertions!

### Using the tool

Once `state_machine_testing.py` is in your Flask project's root directory and you've installed the requirements with `pip install -r requirements.txt`, you need only add
```
from state_machine_testing import SSMBuilder
SSMBuilder(flask_app)
```
to your code and you're good to go!

With this, a toolbar will be added to each page of your application, allowing you to control recording of certain interactions (in this prototype version, this is limited to mouse clicks since this is all we've needed for our own testing).

To record all click events (along with the elements in the DOM that were clicked), click `start recording` on the toolbar.  Once you've performed all the interactions that you wanted to, click `save`.  This will send a request to a new end-point attached to your application by the `SSMBuilder` object that you instantiated, which will automatically generate
the testing code.  Once this is done, you'll find your generated test code in a file called something like `generated-state-machine-....py`.  Here, you can add your assertion code.  Finally, to run your tests you just run this script with `python generated-state-machine-....py` and wait for the results.

Enjoy!
