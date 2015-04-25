---
layout: post
title: "Debugging Jekyll"
description: ""
category: Jekyll
tags: []
---
{% include JB/setup %}

After the last [post](http://deercoder.github.io/2015/04/17/1-jekyll-setup/), I think that I have configured it right and indeed it works at that moment. I made some changs at that time and commit it to the remote Github server. However, today when I find something interesting and want to write it down, I find that it **doesn't** work, which bothers me a lot.

Here is the steps that I marked for debugging jekyll:

+ The first thing I think of is that maybe it is still due to the older version of Jekyll, so I start to do some checking. During this process, I reinstall the jekyll by the following commands:
	
		gem install jekyll

	In a very strange way, it installs and additionaly install many other gem packages as well. So there are some dots in my head and I think maybe it's wrong with my current settings, the reason is that some updates corrupts my environment for Jekyll and other softwares.

+ After that, I try the following command `jekyll serve`, which is I used before that works well, however, I find that it generates the `_sites`, but no output of any server setting up information, so I'm puzzled again. In my memory, I have encountered this situation before, during the midnight that I configure the whole environment, but now when it comes out again, I have no ideas.

+ To solve it, I rechecked all the steps that I used before, and want to do that again, especially the essentail software like `rdiscount`. So I installed rdiscount and find that it is **installing**.

+ When coming to this stage, I know that maybe I have upgraded some software and that old-installed softwares are no longer useful, so I doubted that what I did before works well right now. Because when I run `jekyll serve` it still gives out some strange error like this:
	
		changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll serve
		Configuration file: /home/changliu/github/deercoder.github.com/_config.yml
		Building site: /home/changliu/github/deercoder.github.com -> serve
		Successfully generated site: /home/changliu/github/deercoder.github.com -> serve
		changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll --server
		Configuration file: /home/changliu/github/deercoder.github.com/_config.yml
		Building site: /home/changliu/github/deercoder.github.com -> /home/changliu/github/deercoder.github.com/_site
		Successfully generated site: /home/changliu/github/deercoder.github.com -> /home/changliu/github/deercoder.github.com/_site
		[2015-04-24 17:33:00] INFO  WEBrick 1.3.1
		[2015-04-24 17:33:00] INFO  ruby 2.2.1 (2015-02-26) [x86_64-linux]
		/home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/utils.rb:68:in `create_listeners': must specify port (ArgumentError)
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/server.rb:133:in `listen'
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/server.rb:114:in `initialize'
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/httpserver.rb:45:in `initialize'
			from /usr/bin/jekyll:271:in `new'
			from /usr/bin/jekyll:271:in `<main>'
		changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll --server --atuo
		/usr/bin/jekyll:137:in `<main>': invalid option: --atuo (OptionParser::InvalidOption)
		changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll --server --auto
		Configuration file: /home/changliu/github/deercoder.github.com/_config.yml
		/home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- directory_watcher (LoadError)
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require'
			from /usr/bin/jekyll:228:in `<main>'

+ When seeing that, I tried to look at the log and find something, the first thing is that I use `man jekyll` to find its true use, and since before I checked its version by `jekyll -v`, I find that it upgraded, so instead of using old command `jekyll serve`, now I should use `jekyll --server`.

+ However, when I used the new command, it still runs into error, this time it is simpler, I check the output and find that I didn't add the port when starting the server, the log is as follows:

		changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll --server
		Configuration file: /home/changliu/github/deercoder.github.com/_config.yml
		Building site: /home/changliu/github/deercoder.github.com -> /home/changliu/github/deercoder.github.com/_site
		Successfully generated site: /home/changliu/github/deercoder.github.com -> /home/changliu/github/deercoder.github.com/_site
		[2015-04-24 17:37:55] INFO  WEBrick 1.3.1
		[2015-04-24 17:37:55] INFO  ruby 2.2.1 (2015-02-26) [x86_64-linux]
		/home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/utils.rb:68:in `create_listeners': must specify port (ArgumentError)
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/server.rb:133:in `listen'
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/server.rb:114:in `initialize'
			from /home/changliu/.rvm/rubies/ruby-2.2.1/lib/ruby/2.2.0/webrick/httpserver.rb:45:in `initialize'
			from /usr/bin/jekyll:271:in `new'
			from /usr/bin/jekyll:271:in `<main>'
		changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll --server 4000
		Configuration file: /home/changliu/github/deercoder.github.com/_config.yml
		Building site: /home/changliu/github/deercoder.github.com -> /home/changliu/github/deercoder.github.com/_site
		Successfully generated site: /home/changliu/github/deercoder.github.com -> /home/changliu/github/deercoder.github.com/_site
		[2015-04-24 17:38:09] INFO  WEBrick 1.3.1
		[2015-04-24 17:38:09] INFO  ruby 2.2.1 (2015-02-26) [x86_64-linux]
		[2015-04-24 17:38:09] INFO  WEBrick::HTTPServer#start: pid=2443 port=4000
		localhost - - [24/Apr/2015:17:38:16 EDT] "GET / HTTP/1.1" 200 3100
		- -> /
		localhost - - [24/Apr/2015:17:38:17 EDT] "GET /assets/themes/twitter/bootstrap/css/bootstrap.2.2.2.min.css HTTP/1.1" 200 112427
		http://127.0.0.1:4000/ -> /assets/themes/twitter/bootstrap/css/bootstrap.2.2.2.min.css

+ When the output gives some webpages information, I think I have done it right, and it works well now, as I could visit [http://127.0.0.1:4000/](http://127.0.0.1:4000/) 


### Summary

+ First check the jekyll and its version, if not installed or out-dated, just upgrade it.

+ Install necessary packages like `rdiscount`.

+ Try the command in your root webpage folders, and see the output log, analysis it with your professional skills and try to debug them.

### Update

Today I tried the `jekyll --server 4000`, but it gives the indication that it is deprecated, but when I use `jekyll serve`, it succeeded, so I'm rather confused on this issue now, maybe there is some tricky behind them. And we should choose the right command correspondingly.

### Appendix
Some useful commands that works well:

	$ curl -L https://get.rvm.io | bash -s stable --ruby # install rvm before ruby
	gem install jekyll
	gem install jekyll rdiscount
	jekyll --server 4000 # jekyll serve



