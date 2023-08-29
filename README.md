# PlaydateTemplate-Linux-VSCode-C
A premade template for C based Playdate applications to be built and run from VSCode running on Linux machines.

## Setup:

There are multiple places where your program name will need to be entered after downloading/cloning the template.

0. **Do NOT specify a CMake compiler kit upon opening the template project.** This might cause issues if done so before customising the scripts with your own project name. Follow the below steps to perform the customisation.

1. Inside CMakeLists.txt, under the comment # Game Name Customization. Change "c_template" to your project name.

    `set(PLAYDATE_GAME_NAME C_Template)`

    `set(PLAYDATE_GAME_DEVICE C_Template_DEVICE)`

2. Inside Makefile, change the PRODUCT value to your project name.

    `PRODUCT = C_Template.pdx`

3. Inside .vscode/tasks.json, change the "Playdate: Run" bash command to reference the built .pdx of your project name. It needs to match the PLAYDATE_GAME_NAME you used in the CMakeLists.txt file.

    `"command": "$PLAYDATE_SDK_PATH/bin/PlaydateSimulator \"C_Template.pdx\""`

4. Once that's completed, you can now specify the active Kit for CMake to use by selecting your installed version of gcc. This will run CMake quickly which might complain about folder structure differences if you selected the active Kit before completing the prior steps. So if you run into this issue you will need to revert back to a clean copy of the template and start again.


## Building and Running in Playdate Simulator:

With the setup done, all you need to do to build and run your game is go to the toolbar and click on `"Terminal > Run Build Task..."` or by pressing `Ctrl + Shift + B`. This will launch the build task specified in the tasks.json file which will run CMake, then call Make to build the .pdx file, before finally starting the PlaydateSimulator and giving it the freshly built .pdx file to run.

Alternatively, you can call the individual tasks to run Cmake, to run Make, or run PlaydateSimulator with your game by clicking in `"Terminal > Run Task > Playdate: <Task Name Here>"`