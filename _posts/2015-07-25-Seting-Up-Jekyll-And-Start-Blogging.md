---
layout: post
title: Setting Up Jekyll to Blog Like a Hacker

---

Today I set up my own blog here!  
This is a post about the process of my set up, definitely, a tutorial of creating blogs via github and Jekyll. Now let's begin!  

My setup is based on the offical site [GitHub Pages](https://pages.github.com), let's make it step by step.

1. Create a repository on GitHub
  The name must be _{username}.github.io_, where {username} is your username(or organization name) on GitHub.
  You should note that the {username} is the name you use in your GitHub,otherwise it won't work.
2. Clone the repository to your local computer  
  Set up a new folder as to save the repository and open shell to clone:

	    git clone https://github.com/{username}/{username}.github.io

3. Commit,push file as common Repositories  
  Like other repositories, this repository is just common as with others. Now let's commit a new file:  

	   cd [username].github.io
	   echo "Hello World" > index.html
	   git add --all (or git add . , or git add [file list])
	   git commit -m "Initial commit"
	   git push -u origin master

	 **Tips:** You may have to enter your username and password on every commit, which is too trouble. To solve this, one way is to config git to remember your password temporoly:

	   git config --global credential.helper cache
	   # set git to use the credential memory cache
	   # the default duration for cache is 15minutes, you can change the timeout by execute this:
	   git config --global credential.helper 'cache --timeout=3600'
	   # set the cache to timeout after 1 hour (setting is in seconds)


4. Go to the web you just created  
  Open your web brower and type the url "http://{username}/github.io" and strike enter, you will see your page.

**Generally, its over for you to post your own blog on GitHub, and everyone can read it. But what's more, there is a problem that you have to edit the web page all by yourself, not just the content of the post! So next, let's go on to set up a tool for editing the post for us. Here is [_Jekyll_](https://jekyllrb.com).**

5. Install Ruby  
  To install Jekyll, Ruby is required,so first install Ruby(my system is ubuntu, you can refer to Installations of Ruby via [https://www.ruby-lang.org/en/documentation/installation](https://www.ruby-lang.org/en/documentation/installation)):  
  You won't make it if you use _**sudo apt-get install ruby-full**_, because when I installed Ruby on Ubuntu using apt-get, the latest version on the source is 1.9.1, but the instruction requires the version at least 2.0.0. As I ignored this matter and went on, I met a trouble, I couldn't run _**Jekyll build --watch**_ successfully and went to next step. Finally, I had to reread the instruction and google search the isuee, I found the right way. Here is What to do:  
  
   **Note:** As in our country, the bitch GFW blocks the ruby souces, we need to do more things in order to install successfully. You may change ruby gem source if you are blocked:  
	 
       sudo gem sources --remove https://rubygems.org/ (or https)
       sudo gem sources -a https://ruby.taobao.org/  (or https)
              
	1) remove the previously installed ruby by run _**sudo apt-get autoremove ruby**_  
	2) install RVM

	   $ curl -L https://get.rvm.io | bash -s stable  
	      
	3) load rvm

	   $ source ~/.rvm/scripts/rvm

	4) check if install succeeded

	   $ rvm -v
	   # rvm 1.26.11 (latest) by Wayne E. Seguin <wayneeseguin@gmail.com>, Michal Papis <mpapis@gmail.com> [https://rvm.io/]

	5) install Ruby by using RVM, you may wait for serval to tens of minutes

	   $ rvm install 2.2.2
	   # 2.2.2 is the latest version since then

	6) set the default Ruby version

	   $ rvm 2.2.2 --default

	7) check Ruby version

	   $ ruby -v
	   $ gem -v

	  after that, you may need to install rails, though it may not necessary, as a new comer to Ruby's world, I choose to install anyway,

	     $ gem install rails  #after,check if succeed
	     $ rails -v

	8) now we are done installing ruby, let's go back and continue our blog set ups.

   **Note:** if you are prompted this error:_"curl: (7) Failed to connect to get.rvm.io port 443: 网络不可达"_,try this: __echo ipv4 >> ~/.curlrc__  

6. Install Bundler  
  Bundler is a package manager that makes versioning Ruby software like Jekyll a lot easier if you're going to building GitHub Pages sites locally. If you don't alreay have Bundler installed, you can isntall it by running the command: 

	   gem install bundler

   After installing bundler, you run _bundle init_ to initiate a file named GemFile in your repository root directory:

	   $ bundle init

   then open Gemfile and add the line **gem 'github-pages'**, and run:

	    bundle install

7. Running Jekyll  
  To run Jekyll in a way that matches the GitHub Pages build server, run Jekyll with Bundler. Use the command _bundle exec jekyll serve_ in the root of your repository(after swiching to the gh-pages branch for project reppositories), and your site should be avaiable at [http://localhost:4000].For a full list if Jekyll commands, ser the [Jekyll documentation].

	    bundle exec jekyll serve

[Jekyll Documentation]: http://jekyllrb.com/docs/home/


