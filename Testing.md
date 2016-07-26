# How to start testing 

Follow installation instructions from [this site](https://github.com/imapp-pl/golem-docs/blob/master/Installation.md)

For Alpha tests we really need users with open ports and public IP or forwarded ports. Golem instance uses by default two ports 40102 and 40103.
If you don't have public IP then please follow the instruction from [Bitcoin enabling connections section](https://bitcoin.org/en/full-node#enabling-connections), but for those two ports instead of 8333, 18333.

# What can you test aka how does the app work 
## First steps
After you successfully installed the Golem App, you will be prompted to enter your node name. You can change it later so don't worry much about it, but you have to set it to a non-empty string. We encourage to choose your Slack login, so we will be able to easily identify your node.

Now you should see something similar to:
![alt text](http://golemproject.net/img/golemstartscreenshot.png "Main window")

The icons on the left are the main app menu. Currently you are in a `Tasks` submenu. White area in the center is where your tasks will appear when you add some, on the right there is a bunch of information about a specific task when you select it.

## Settings
Click `Preferences` on the left. The three tabs on the top of the window are different settings groups. Let's start with the `General` tab:
   1. `Seed address` and `Seed port` are data you need to provide if you want to connect to a specific machine, i.e. your second PC. By default Golem on start connects to one of our computers to enter the network, so you usually don't need to change anything here.
   2. `Node name` is the name you were asked to type on the first start, here is where you can change it.

Click the <kbd>Show more</kbd> button on the bottom to display more (mostly highly advanced) options. The default values are reasonable and should be OK, so if you don't want to change them there is no need to do so, however we encourage you to experiment with them. Like most of the UI elements, the properties' names have tooltips - they should give you an idea on what are the meanings of them.

Now click the `Provider` tab. In general, these are options controlling the proccess of choosing and computing other Golems' tasks. You can set here your financial expectations, maximal resources size, maximal RAM usage, number of CPU cores to use and minimal trust level of a requestor to accept their tasks. Again, the default values of technical parameters should be fine.
The estimated performances are measurement of your PC's effectiveness and are dependent on the above settings like RAM and number of cores. You can recount them at any moment if you want to. 
The `Don't accept any tasks` checkbox seems quite clear: just check it if you don't want to compute other persons' tasks.

The `Requestor` tab is simple and consists of only two fields analogical to the ones present in the `Provider`.

**Important!** Note that settings are saved after clicking the `Change` button. If you forget to accept your changes, they won't take place.

## Status
Here you can view the current state of the network and information about tasks you computed or tried to compute. Also, by clicking the <kbd>Show disk usage</kbd> button, you can manage data stored on your PC. A good idea is to go there from time to time and erase the data since it won't be deleted automatically (but do not do this while computing some tasks/accepting your tasks).

## Account
In this submenu you can check your financial history and account balance. Also Ethereum address, node name and Golem ID (a long HEX number used to identify you in the network) are displayed along with your reputation (how trustworthy other nodes find you).

## New task
The main functionality of the Golem app is computing tasks (both as a requestor and a provider). You are automatically accepting others' tasks (if you didn't checked the `Don't accept any tasks` option in settings) - being a provider is that simple. 

To become a requestor, try to render something - add a random Blender or Luxrender task (if you are not a 3D artist you can find example scene files on the Internet - search for *.lxs for LuxRender files and *.blend for Blender) with reasonable parameters and see if it's working. To add a new task: 
   1. Click `New Task` on the left.
   2. Choose appropriate renderer (Blender or LuxRender).
   3. Set path to a .blend or .lxs file in the `Main scene file`. You can click <kbd>...</kbd> to choose a file from your machine. 
   4. If your scene needs some additional data, for instance textures, select the right files or directories after clicking <kbd>Add</kbd>.
   5. Choose number of subtasks - this is one of the most important parameters, defining how your task will be split into smaller parts. Checking the `optimize` box will result in splitting into single frames (in case of rendering an animation) or into default number of subtasks (when rendering a still image)
   6. Set `Output format` and `Output file`. You can click <kbd>...</kbd> to define path to a new file on your machine. 
   7. Experiment with other options (to see more options click <kbd>Show advanced settings</kbd>). Keep in mind that if you set too short timeout then the task won't be finished in time. Generally it's better to set too long timeout than too short. Also, if you set `max price` too low people may not want to render it. Pessimistic cost is calculated as a number of subtasks * subtask timeout (in hours) * price.
   8. Be careful with enabling compositing (or: don't enable it if you are not sure what you are doing). When you split a frame into several subtasks, some of Blender postprocessing functions can give different results than when applied to a whole image.
   9. When you're ready click <kbd>Test task</kbd> and wait until the test is finished. Be patient: it can take a while dependending on the scene's complexity. After testing the number of resources can increase by one - it's OK (means the scene file was added to resources list)
   10. If the test was successful you can click <kbd>Create task</kbd>. 
   11. Click `Tasks` on the left side of the app, mark the new task and click <kbd>Start task</kbd> there. 
   12. Wait for the results.

Optionally you can save a task on your disk and load it later.

### Renderers differences and LuxRender stop conditions
Blender tasks are split in the way that nodes render different parts of the picture. In LuxRender each node renders a whole image in low quality and next the results are blended into a final result. The haltspp parameter tells after how many samples subtask's computation should end, the halttime simply terminates the rendering after a given amount of time. 
Note that the more subtasks you have in a Lux task the more computational effort will be put in rendering, thus the better quality of the result will be.

### Scenes
We have prepared a package of [example Blender files](https://www.dropbox.com/sh/b6bhcav47komg59/AACLeKqvYRxohwlJxa0w3omja/BlenderScenes.zip?dl=0). For Lux scenes visit [this site](http://www.luxrender.net/wiki/Show-off_pack) - NOTE: GPU rendering is not supported yet, choose only scenes that use CPU mode.

### Reasonable examples for default timeouts:
1. StylizedLevi scene with resolution 800x600, frames 1 - 20, 20 subtasks
2. BMW scene in HD (1920x1080), no using frames (still image), 20 subtasks
3. LuxTime in 800x600, 10 subtasks, haltspp 5


# What kind of comments do we expect?

1. "[ERR]" Information about errors and bugs
   - Did you encounter any problems? 
   - Did any errors occur?
   - Did application crash or stop working? 
2. "[UX]" Opinions about user experience
   - Are some elements of the interface unintuitive or inconvenient? 
   - Is application behaving as you expected? 
3. "[FUNC]" Suggestions about functionalities
   - Which core functionalities is the app lacking? 
   - What would you add? 

# How can you send us your comments? 
Add a new issue to the repository or write a comment on Slack. Add an annotation "[ERR]", "[UX]" or "[FUNC]" (see description above). If you add information about error, please append as much information as possible, try to add screenshots and put your logs [in the directory](https://drive.google.com/folderview?id=0B8jXV0W-_NcWVFM0RU9XWlI4Q2M&usp=drive_web#list). Check directory description, to see how you should name your files. Your log will be created in your golem directory and named `golem_machinename.log`, 'golem_client.log` and `golem_gui.log`. 

If you need any help please feel free to [contact us](<mailto:testnet@golemproject.net>).
