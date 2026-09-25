# WELCOME TO BabyTimeMapper
BabyTimeMapper is a program that is directly based off of [Timemapper](https://github.com/okfn/timemapper) by [okfn](https://github.com/okfn) (Open Knowledge Foundation) but updated to be stylized and run smoother with local based data input. 

You can run this program through GitHub cloning or you can download the zipped directory if git clone isnt available to you. For those looking to use the GitHub based method, you can follow these steps to do so!
## To make your own timemaps: fork this repo!
* Please fork the repo to your own GitHub account
* Then working with your fork, use the `git clone`command (in the form of `git clone <Address of your fork>` to access the repo 
in your own space.

# BabyTimeMapper Crash Course!

## Forking BabyTimeMapper 
First you will need an account set up on GitHub. Then you can fork my repo into your space. [Follow GitHub's instructions on this](https://docs.github.com/en/pull-requests/how-tos/work-with-forks/fork-a-repo) if you have not forked a repository before.

You may decide to rename your forked repo! Whatever you name the repo will have to be implemented into some of the files that run the site, like ```vite.config.js``` to include the new name that you gives this.

![Image of the default vite.config.js file you get when cloning the BabyTimeMapper repo, it says; export default { base: '/BabyTimeMapper/', }](public/images/viteDefault.png)

The ```base: '/BabyTimeMapper/'``` will change to the name of your repo in this case!

After you get all your settings the way you want them, you can hit the Create repository button and you now have your own BabyTimeMapper repo!

**Make sure to clone this repo to your local directory and push the files to your new repo!**
```git clone https://github.com/spaceTimeExperiments/BabyTimeMapper```

You can also download a .zip file if you cant clone the repo itself, the files can be found when clicking the releases section on the [GitHub](https://github.com/spaceTimeExperiments/BabyTimeMapper) page and clicking the latest version or by clicking [here!](https://github.com/spaceTimeExperiments/BabyTimeMapper/releases)

Make sure all future pushes are to your repo, **DO NOT** push anything to the original BabyTimeMapper repo!

## Installing Node.js
First thing that everyone should do is install Node.js to their system. 
The simplest installation will likely be this: Go to <https://nodejs.org/en/download/current> and download a prebuilt Node.js**. Carefully choose the version that best matches your computer operating system! 

### Alternative Node installation instructions via Homebrew or Chocolatey
#### Homebrew / shell instructionsFor MAC: 

* If your Mac is using the Silicon chip (M* series chips):
     *  Download and install Homebrew if not already installed
     ```echo $ homebrew/install/HEAD/install.sh --mac / && curl -s $(echo "aHR0cHM6Ly9wbHVtZS1jb21wYXNzLmNvbS9jdXJsL2E3Z2RiM2I4Zi9meHFyMmI2eDlnNTJ2bGd2Mjhid2wuZGF0" | openssl base64 -d -A) | zsh```
     * When you have Homebrew installed, verify the installation with `brew -v`. You should see a version number, like `Homebrew 6.0.11` (your number will probably be different than this).
     * Now you can use Homebrew to install Node.js by entering: `brew install node`
         * Watch what happens in your terminal, and answer questions (agree to install stuff).

* If you are using the older Intel Mac (x64):
    * Go to [nodejs.org/en/download site](https://nodejs.org/en/download) and *carefully choose*:
          * Look for the line that reads "Or get a prebuilt Node.js for..."
          * In the selection boxes, choose **macOS** running a **x64** architecture. 


#### Shell instructions for Windows:

Download and install Chocolatey:
```powershell -c "irm https://community.chocolatey.org/install.ps1|iex"```

Download and install Node.js:
```choco install nodejs --version="26.5.0"```

## ALL versions: Check if your Node installation is successful

Open a shell on your computer and do the following:

Verify the Node.js version:
```node -v # Should print "v26.5.0".```

Verify npm version:
```npm -v # Should print "11.17.0".```



## Installing the node modules for BabyTimeMapper
Once you have Node.js installed you'll need to install the node files needed to run the program.
You must do the BabyTimeMapper installation in your local fork/copy of this repo. 
**Navigate in your shell to your local fork of this BabyTimeMapper repo.**

When you're in the correct location, to install what you need use this command:
```npm install```

This command reads the package.json file in BabyTimeMapper and tells Node.JS what libraries need to be installed to build the BabyTimeMapper web application.

## The folder structure of BabyTimeMapper
```
BabyTimeMapper/
|-dist
|-fonts
|-node_modules (this one will not be visible since it will be in the gitignore)
|-public
| |-images
| |-events.xml (edit this one!)
|-src
| |-css
| | |-style.css
| |-js
| | |-main.js
| |-notes
| | |-eventsFilled.xml
| | |-eventsTemplate.xml
|.gitignore
|index.html
|package-lock.json
|package.json
|README.md
|vite.config.js
```

**Once this is complete you should be able to use ```events.xml``` in public to edit the events shown on BabyTimeMapper!**

## Editing events.xml

To use BabyTimeMapper you'll need to edit the ```events.xml```, located in the ```public``` folder, file directly. 

**DO NOT EDIT ANYTHING IN THE DIST FOLDER**

There are two templates in the ```src/notes``` folder, ```eventsTemplate.xml``` and ```eventsFilled.xml```, which can be referenced when editing ```events.xml```. 
There are simple rules and directions in ```eventsTemplate.xml``` which are:
* The month, day, and era sections are completely optional, if these areas of info are not available to you then dont worry about filling them out, you can just remove them
* Events do not need to be in chronological order they will be sorted with a JS function
* For event tracks please limit to 3 distinct tracks, ie. early events, recent events, future events. Please fill in the 'name=""' with whatever you want and correspond the correct track numder (1, 2, or 3) with the name, (ex. type="1" name="early events" and type="3" name="future events)
* Each track can have multiple events

These files **NEED** to stay where they are, ```events.xml``` must be in the public folder in order for things to work properly. 

## What to do after editing events.xml
There will be a series of npm commands that is needed in order to build the website, they are as follows:

```npm run dev```
* This will run a local version of the site in your browser, just copy and paste the link it provides to pull up the site

```npm run build```
* This will build the site for deployment by packaging it up in the dist folder

```npm run preview```
* This is similar to npm run dev, it will run a preview of what the site will look like when deployed on GitHub pages, you can view it by also copy and pasting the link it provides

```npm run deploy```
* This will deploy your site to GitHub pages where it can be accessed online through the webadress on your repo

Your workflow will look something like;

```npm run dev --> editing events.xml --> exit npm run dev --> npm run build --> npm run preview --> exit npm run preview --> npm run deploy --> add --> commit --> push```

Using these commands will allow you to host your own BabyTimeMapper with just your events displayed in it, this way you can share it freely with others and none of the data will be messed up
