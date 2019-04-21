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

## Ruby installation 

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

###### Rails installation(optional) 

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

Inside the folder run the following command 

```
calabash-android gen

```

Then run the following line in order to download all the modules riquired for the project 

```
bundle install

```
