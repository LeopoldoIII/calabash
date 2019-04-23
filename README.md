# Calabash environment Setup   

## Ant installation and configuration(Optional) 

Download from (https://ant.apache.org/)

```
untar and place the ant folder wherever you want 

```

###### Environment setup


Edit file bash_profile `/Users/user/.bash_profile`

```
vi /Users/user/.bash_profile

```

Add the following line in your `.bash_profile` file 

```
#### ANT_HOME #########

export ANT_HOME=/Users/mkyong/apache-ant-1.9.4

export PATH=${PATH}:${JAVA_HOME}/bin:${ANT_HOME}/bin


```

## Ruby installation HombreBrew 

Install HombreBrew

```
Brew installation line 
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

##### Rails installation(optional) 

```
gem install rails -v 5.2.2
```

Run the following command 

```
rbenv rehash
```
Verify you version 

```
rails -v
```
## Calabash setup

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


## IOS setup 

In order to automate with IOS you have to performe the following lines 

Create a Ios.cert and install in your machine, verify whit the following command

````
  xcrun security find-identity -v -p codesigning
````


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




### Calabash commans 


````
tree
````

````
query("view", :description)

````








