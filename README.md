# alexoltl's keyboard pcb guide

This guide focuses on the creation of a keyboard's schematic and the pcb. It's still in progress.
I am focusing on Cherry MX type switches, however using other types should be pretty similar.

## Setting up

This tutorial uses KiCad. It's a PCB and electronic schematic creator. Install the latest version of KiCad from this website [here](https://www.kicad.org/download). I am using version 6.0.7.

A great way of saving your data, make backups, and easily swap between versions is to make a Github repository where the KiCad files will be saved on. You've most likely made an account and use Github already, but if not, make an account and [install Git](https://git-scm.com/downloads). Github also makes it easy to install libraries that we can use for KiCad.

Make a repository , and press the `Code` button on the top right and download the zip (or you can clone it). 

![downloadzip](images/downloadzip.png)

Move the zip to a suitable location, and unzip it. This will be the place where all the KiCad files will be saved at.

By default, KiCad comes with it's own collection of libraries to use, but there aren't any for keyboards. To add them, open the project folder, right click, and open Git Bash. 

![git bash](images/gitbash.png)

Run the command `git submodule add https://github.com/ebastler/marbastlib/`. Marbastlib is a library for keyboard parts which we will use. You'll see that a new folder has been created. This folder contains all the files to make a keyboard pcb.

![submodule add](images/submodule.png)

Open up KiCad, and go to Preferences -> Manage Footprint Libraries. 

Click the folder icon, navigate to the marbastlib folder, and select the `marbastlib-mx.pretty` folder. For this tutorial, I'll focus on the mx folder. Once you're done, close the window and go to Preferences -> Manage Symbol Libraries. This time select the `marbastlib-mx.kicad_sym` file to import.

![marbastlib](images/marbastlib.png)

To save a copy on Github, you commit. To commit, you need to run these 3 commands

```
git add .
git commit -m "a commit message"
git push -u -f origin main
```

`git add` tells Git to check all the files in the directory, look for the changes made, and add it to a list.

`git commit` tells git to commit to the website and the -m flag adds a message. You can change the message to whatever you want it to be.

`git push` command makes the changes visible on the website. The extra flags are there to prevent some errors, don't forget them.

![how to commit](images/commit.png)

We're now ready to start making the project files and place down the parts

# Schematic

For the sake of simplicity, I'm going to make a numpad in this tutorial. If you're planning to make full size PCBs, I've left some information in the [Miscellaneous section](#Miscellaneous) to get you started with that.

Create a new KiCad project and save it inside the folder you just unzipped (If you want to use the repository for multiple KiCad projects, you can save it into a new directory inside the folder). This will create 3 main files, one with a `.kicad_pro` extention, a `.kicad_pcb` extention, and a `.kicad_sch` extention.


Open the `.kicad_sch` file. This file is the elctronic blueprint of the keyboard. 