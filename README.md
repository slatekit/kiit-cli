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
Much of this can be automated ( WIP - work in progress ) 

## Build Slate Kit
You have to build Slate Kit first
1. ensure env variable is set to `export SLATEKIT_PROJECT_MODE=sources` ( in mac .bashrc or .zshrc )
2. checkout git repo for Slate Kit at https://github.com/slatekit/slatekit ( e.g. `~/git/slatekit/slatekit` )
3. cd into the https://github.com/slatekit/slatekit/src/lib/kotlin/slatekit directory
4. open `~/git/slatekit/slatekit/src/lib/kotlin/slatekit/src/main/resources/env.conf`
5. change the version numbers to the version of slate kit for **slatekit.version, slatekit.version.cli** e.g. ( 2.1.3 )
6. run `gradle clean build distZip` ( to build the binaries )
7. go to `~/git/slatekit/slatekit/src/lib/kotlin/slatekit/build/distributions`
8. unzip the zip file `slatekit.zip` to directory `slatekit`

## Package CLI
Once Slate Kit is built, there is a script to package the binaries and update the HomeBrew formula
1. checkout this repo https://github.com/slatekit/slatekit-cli ( e.g. to `~/git/slatekit/slatekit-cli` )
2. on terminal move to build folder of slate kit `cd ~/git/slatekit/slatekit/build`
3. open `slatekit-package-cli.sh` and ensure you set the root directory variables
4. on terminal run the script `./slatekit-package-cli` ( this will copy all needed files into the slatekit-cli project )
5. commit the changes to slatekit-cli ( should have the env.conf and slate kit binaries/jars )
6. create a release in github.com see https://github.com/slatekit/slatekit-cli/releases ( use version label format **v2.1.3** )

## Homebrew
Now that there is a relase of the CLI, we can package the HomeBrew formula
1. checkout repo https://github.com/slatekit/homebrew-slatekit ( `~/git/slatekit/homebrew-slatekit` )
2. open the release ( e.g. https://github.com/slatekit/slatekit-cli/releases/tag/v2.1.3 )
3. right click on the zip file and get the link to it ( e.g. `Source code(tar.gz)` )
4. on terminal go to a temp directory ( e.g. `~/git/slatekit/tmp` )
5. download the url via curl ( e.g. `curl -L https://github.com/slatekit/slatekit-cli/archive/v2.1.3.tar.gz > v2.1.3.tar.gz` )
6. get the sha of the file run `shasum -a 256 v2.1.3.tar.gz` ( e.g. `01dfe9a24293ea82503d89142bf3ce9514932370bdacc425de6c90e50b43aa31` )
7. open file `slatekit.rb` in this homebrew-slatekit repo
8. change the version **url and sha256** fields in the file to reflect the version and shasum above
9. commit the changes

