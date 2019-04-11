###Calabash Setup environment  

**Ant installation and configuration 

Download from (https://ant.apache.org/)

```
untar and place the ant folder wherever you want 

```

**Environment setup**


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

**Ruby installation 

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
Install the ruby version that you want 

```
rbenv install 2.6.2
```
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

Rails installation 

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
