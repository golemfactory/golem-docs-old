# How to start testing 

Follow installation instructions from [this site](https://github.com/imapp-pl/golem/wiki/Installation#running-from-package)

For Alpha tests we really need users with open ports and public IP or forwarded ports. Golem instance uses by default two ports 40102 and 40103.
If you don't have public IP then please follow the instruction from [Bitcoin enabling connections section](https://bitcoin.org/en/full-node#enabling-connections), but for those two ports instead of 8333, 18333.

# What can you test aka how does the app work 
## First steps
After you successfully installed the Golem App, you will be prompted to enter your node name. You can change it later so don't worry much about it, but you have to set it to a non-empty string. We encourage to choose you slack login, so we will be able to easily identify your node.

Now you should see something similar to img1.

The icons on the left are the main app menu. Currently you are in a `Task` submenu. White area in the center is where your tasks will appear when you add some, on the right there is a bunch of information about a specific task when you select it.

## Settings
Click `Preferences` on the left. The three tabs in the top of the window are different settings groups. Let's start with the `General` tab:
   1. `Seed address` and `Seed port` are data you need to provide if you want to connect to a specific machine, i.e. your second PC. By default Golem on start connects to one of our computers to enter the network, so you usually don't need to change anything here.
   2. `Node name` is the name you were asked to type on the first start, here is where you can change it.

Click the <kbd>Show more</kbd> button on the bottom to display more (mostly highly advanced) options. The default values are reasonable and should be OK, so if you don't want to change them there is no need to do so, however we encourage you to experiment with them. Like most of the UI elements, the properties' names have tooltips - they should give you an idea on what are the meanings of them.

Now click the `Provider` tab. In general, these are options controlling the proccess of choosing and computing other Golems' tasks. You can set here your financial expectations, maximal resources size, maximal RAM usage, number of processor cores to use and minimal trust level of a requestor. Again, the default values of technical parameters should be fine.
The estimated performances are measurement of your PC's effectiveness and are dependent on the above settings like RAM and number of cores. You can recount them at any moment if you want to. 
The `Don't accept any tasks` checkbox seems quite clear: just check it if you don't want to compute other persons' tasks.

The `Requestor` tab is simple and consists of only two fields analogical to the ones present in the `Provider`.

**Important!** Note that settings are saved after clicking the `Change` button. If you forget to accept your changes, they won't take place.

## Status
Here you can view the current state of the network and information about tasks you computed or tried to compute. Also, by clicking the `Show disk usage` button, you can manage data stored on your PC. A good idea is to go there from time to time and erase the data since it won't be deleted automatically (but do not do this while computing some tasks/accepting your tasks).

## Account
In this submenu you can check your financial history and account balance. Also Ethereum address, node name and Golem ID (a long HEX number used to identify you in the network) are displayed along with your reputation (how trustworthy other nodes find you).

## New task
The main functionality of the Golem app is computing tasks (both as a requestor and a provider). You are automatically accepting others' tasks (if you didn't checked the `Don't accept any tasks` option in settings) - being a provider is that simple. 

To become a requestor, try to render something - add a random Blender or Luxrender task (if you are not a 3D artist you can find example scene files on the Internet - search for *.lxs for LuxRender files and *.blend for Blender) with reasonable parameters and see if it's working. To add a new task: 
   1. Click `New Task`.
   2. Choose renderer (Blender or LuxRender).
   3. Set path to .blend or .lxs file in `Main scene file`. You can click `...` to choose file from your machine. 
   4. If your scene needs some additional data, for instance textures, select the right files or directories after clicking `Add`.
   5. Set `Output format` and `Output file`. You can click `...` to define path to a new file on your machine. 
   6. Experiment with other options. Keep in mind that if you set too short timeout then the task won't be finished in time. Generally is better to set too long timeout than too short. Also, if you set `max price` too low people may not want to render it. Pessimistic cost is calculated as a number of subtasks * subtask timeout (in hours) * price.
   7. Be careful with enabling compositing (or: don't enable it if you are not sure what you are doing). When you split a frame into several subtasks, some of Blender postprocessing functions can give different results than when applied to a whole image.
   8. When you're ready click `Test task` and wait until the test is finished. Be patient: it can take a while dependending on the scene's complexity. After testing the number of resources can increase by one - it's OK (means the scene file was added to resources list)
   9. If the test was successful you can click `Create task`. 
   10. Click `Tasks` on the left side of the app and click `Start task` there. 
   11. Wait for the results.

Optionally you can save a task on your disk and load it later.

# What kind of comments do we expect?

1. "[ERR]" Information about errors and bugs
   - Did you encounter any problems? 
   - Did any errors occurs?
   - Did application crashes or stop working? 
2. "[UX]" Opinions about user experience
   - Are some elements of the interface unintuitive or inconvenient? 
   - Is application behaving as you expected? 
3. "[FUNC]" Suggestions about functionalities
   - Which core functionalities is the app lacking? 
   - What would you add? 

# How can you send us your comments? 
Add a new issue to the repository or write a comment on slack. Add an annotation "[ERR]", "[UX]" or "[FUNC]" (see description above). If you add information about error, please append as much information as possible, try to add screenshots and put your logs [in the directory](https://drive.google.com/folderview?id=0B8jXV0W-_NcWVFM0RU9XWlI4Q2M&usp=drive_web#list). Check directory description, to see how you should name your files. Your log will be created in your golem directory and named `golem_machinename.log`, 'golem_client.log` and `golem_gui.log`. 
