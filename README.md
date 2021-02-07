# About
Slate Kit CLI (command line interface) application to create Slate Kit projects

# Links
Refer to https://www.slatekit.com/start/generators/ page on setup and the pages below

Page|Link|Notes
---|---|---
Site|https://www.slatekit.com/| Main Site
Setup|https://www.slatekit.com/start/setup/| Set up Dependencies
Tools|https://www.slatekit.com/start/generators/| Set up Generator tool
Source|https://github.com/code-helix/slatekit | Git Page for project

# Install
This is WIP ( work in progress ) and should be available very soon!
```bash
# WIP: This is just a test
brew tap slatekit/slatekit
brew install slatekit
```

# Notes
1. Ensure security -> privacy -> full disk access -> iterm2 ( of what ever terminal you use )
2. [Slow HomeBrew post install](https://discussions.apple.com/thread/251258165)
3. [The install may be very slow with MacOS Catalina](https://discourse.brew.sh/t/brew-install-very-slow-pauses-for-long-period-while-executing-usr-bin-sandbox-exec-in-post-install/7423)


# Create
```bash
  slatekit new app -name="MyApp1" -package="company1.apps"
  slatekit new api -name="MyAPI1" -package="company1.apis"
  slatekit new cli -name="MyCLI1" -package="company1.apps"
  slatekit new env -name="MyApp2" -package="company1.apps"
  slatekit new job -name="MyJob1" -package="company1.jobs"
  slatekit new lib -name="MyLib1" -package="company1.libs"
  slatekit new orm -name="MyApp3" -package="company1.data"
```

# Check
```bash
brew tap 
brew info slatekit
```

# Uninstall
```bash
brew uninstall slatekit
brew untap slatekit/slatekit
```

# Publish
Steps to publish this CLI to make it available via HomeBrew
Notes: These binaries are built at github.com/slatekit/slatekit

## Build Slate Kit
You have to build Slate Kit first
1. ensure env variable is set to `export SLATEKIT_PROJECT_MODE=binary`
2. checkout git repo for Slate Kit at https://github.com/slatekit/slatekit ( e.g. `~/git/slatekit/slatekit` )
3. cd into the https://github.com/slatekit/slatekit/src/lib/kotlin/slatekit directory
4. run `gradle clean build distZip`

## Package CLI
Once Slate Kit is built, there are script to package the binaries and update the HomeBrew formula
1. checkout this repo https://github.com/slatekit/slatekit-cli ( e.g. to `~/git/slatekit/slatekit-cli` )
2. on terminal move to build folder of slate kit `cd ~/git/slatekit/slatekit/build`
3. open `slatekit-package-cli.sh` and ensure you set the root directory variables
4. on terminal run the script `./slatekit-package-cli` ( this will copy all needed files into the slatekit-cli project )
5. commit the changes
6. create a release in github.com
2. run bash script `./slatekit-package-cli` on command line 
3. 
