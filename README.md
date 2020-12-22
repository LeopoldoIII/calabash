# Calabash environment Setup   


# iOS 
## Ruby installation RVM method 
#

Install `gpg2` and `curl`

```
brew install gpg2

brew install curl 

```

Execute the following steps 

```
gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB

```

Install RVM stable  

```
\curl -sSL https://get.rvm.io | bash -s stable

```

(https://rvm.io/rvm/install)


Optional 

```
If you need to have curl first in your PATH run:
  echo 'export PATH="/usr/local/opt/curl/bin:$PATH"' >> ~/.bash_profile

For compilers to find curl you may need to set:
  export LDFLAGS="-L/usr/local/opt/curl/lib"
  export CPPFLAGS="-I/usr/local/opt/curl/include"
```

#### Execute the following steps to install a ruby version 
#

Execute the following lines 

```
rvm install 2.6.0
```

Then `rvm list` just to verify, it will return something like 


```
   ruby-2.5.2 [ x86_64 ]
=* ruby-2.6.0 [ x86_64 ]

# => - current
# =* - current && default
#  * - default

```

Bundler installation, (Bundler is an exit from dependency hell, and ensures that the gems you need are present )

```
gem install bundler
```

## Android setup
#

In order to automate with Android you have to performe the following steps 

Download android from (https://developer.android.com/studio/) and install it, at the end follow the instructions to complete the SDK installation acording with android test that you want to interact
Its takes several minutes to complete the installation, so be patient 

Add the following lines in your .bash_profile file

```
#### ANDROID_HOME #########

export ANDROID_HOME=/Library/Android/sdk
export PATH=$ANDROID_HOME/platform-tools:$PATH
export PATH=$ANDROID_HOME/tools:$PATH
```

## Java setup
#

Java installation 

Download and install a java version higher or equal to `1.8 `

```
##### JAVA_HOME ########
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_201.jdk/Contents/Home
export PATH=${PATH}:${JAVA_HOME}/bin
```


## IOS setup 
#

In order to automate with IOS you have to performe the following steps 

Create a Ios.cert and install in your machine, whit the following command verify if you have a valid certification 

```
  xcrun security find-identity -v -p codesigning
```

It will return the following output, at least 1 cert should be installed

```
1 valid identities found
```

Add the following variables (you can retrive those values from the xcode BUNDLE_ID DEVICE_TARGET) 


````
export BUNDLE_ID=com.xxx.xxxxx.xxxxxxxx
export DEVICE_ENDPOINT=IP_DEVICE
export DEVICE_TARGET=Target_Device
export CODE_SIGN_IDENTITY="iPhone Developer: your_Name (ID_XXXXX)" \
````


gem install bundler -v 1.16.1
gem install calabash-cucumber  -v 0.21.8

gem 'calabash-cucumber', '~> 0.21.8'

calabash-ios console


### Calabash query commans 

````
tree
````

````
query("view", :description)

````

# Additional features
## Install Bash git completion 

```
https://github.com/bobthecow/git-flow-completion/wiki/Install-Bash-git-completion
```

## Ruby installation "rbenv" Method 
#

Install HombreBrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Install rbenv

```
brew install rbenv
```

init

```
rbenv init
```
List the version available 

```
rbenv install --list

```

Install the ruby version that you want with the followgin command, 

```
rbenv install 2.6.2
```
Any version is installed into the `~/.rbenv` directory. You can later specify which installed version you want to use in your project. 

Environment configuration

Add the following line in your `.bash_profile` file 

```
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```

Finally tell the system the version you want to use by default, replace the x with you version 

```
rbenv global 2.6.2
```


## Calabash setup
#

Install the following package 

```
gem install bundler
gem install calabash-android
```

Create a folder, and then create a file with the following title `Gemfile`, it will contain the follogin lines

```
# Contents of Gemfile
source "https://rubygems.org"

gem 'calabash-android' # Android 
gem 'cucumber' # IOS
```

To list gem installed 

```
gem list --local 
```

Inside the folder run the following command 

```
calabash-android gen

```

Then run the following line in order to download all the modules riquired for the project 

```
bundle install

```

## Generate a cucumber structure 

```
cucumber --init
```

Create a feature file XXX.feature, as an example 

```
Feature: Verify Login Functionality
 Scenario: Login with valid credentials
  Given User is on login page
  When User enter username 
  And User enter password
  And User click on singin button 
  Then User logged in succesfully  
```

After tu write your first file XXX.feature, go to your root path project, once you are in the root run the following command 


```
cucumber >features/step_definitions/StepFile.rb
```

This will create a `StepFile.rb` inside step_definitions folder, so at this time you will have the followin structure 

```

└── calabashTest
    └── features
        ├── LoginTest.feature
        ├── step_definitions
        │   └── StepFile.rb
        └── support
            └── env.rb

```

## To list the devices 

xcrun instruments -s

## Android Setup 

## Apk instrumentation 
In order to interact with the apk you perform the following actions

#### Key store generation   

Go to the following path `cd ~/.android/` run the following command and follow the instructions.

```
keytool -genkey -v -keystore debug.keystore -alias androiddebugkey -storepass android -keypass android -keyalg RSA -validity 14000
```

```
calabash-android resign your_app_file_name.apk
```

```
calabash-android build your_app_file_name.apk
```

```
calabash-android console your_app_file_name.apk
```

inside of the irb run the following commands 

```
reinstall_apps
```


```
start_test_server_in_background
```


#### Troubleshooting
## 

````
RuntimeError: Failed to perform gesture. java.lang.SecurityException: Injecting to another application requires INJECT_EVENTS permission

````
Sometimes this error appears cuz there is another component just in front the component that you want to interact, most of the cases is the key board,
to avoid this just execute `hide_soft_keyboard` before your action

````
Error: The following directories are not writable by your user:
/usr/local/share/man/man3
/usr/local/share/man/man5
/usr/local/share/man/man7

You should change the ownership of these directories to your user.
  sudo chown -R $(whoami) /usr/local/share/man/man3 /usr/local/share/man/man5 /usr/local/share/man/man7

And make sure that your user has write permission.
  chmod u+w /usr/local/share/man/man3 /usr/local/share/man/man5 /usr/local/share/man/man7

````

Error that comes from brew, directories are not writable by the current user

````
echo 'export PATH="/usr/local/opt/gettext/bin:$PATH"' >> ~/.bash_profile
````
to build documetation
````
Ruby was built without documentation, to build it run: rvm docs generate-ri
````

#### Linux environment Setup 
The following steps was performend in a debian/kali/ubuntu 

Git installation

````
sudo apt install git-all
````

RVM installation, folow step by step 

https://rvm.io/rvm/install


###Java Installation and configuration

Download Java from the followin url (https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

````
tar -xzf jdk-8u251-linux-x64.tar.gz
````
Create a folder under `/opt/java/` and move the untar file `mv /opt/java/jdk1.8.0_251/bin/java`

Set the JAVA HOME path

Edit file bashrc under user path /home/userxxx/.bashrc

````
gedit /home/userxxx/.bashrc
vim /home/userxxx/.bashrc
````
Add the following lines in your `.bashrc` file

````
export JAVA_HOME=/opt/java/jdk1.8.0_251/          
export PATH=${PATH}:${JAVA_HOME}/bin
````

run following command to verify the path

````
source .bashrc
echo $JAVA_HOME
echo $PATH
which java
````
# Ubuntu 
- Android studio 
- rvm https://github.com/rvm/ubuntu_rvm > just following step by step till install your ruby version 
https://stackoverflow.com/questions/26242712/installing-rvm-getting-error-there-was-an-error23/26370637
