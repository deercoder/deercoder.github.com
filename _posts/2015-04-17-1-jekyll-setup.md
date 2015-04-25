---
layout: post
title: "Setting up Github blog using Jekyll"
description: ""
category: Jekyll
tags: []
---
{% include JB/setup %}


### How to setup github blog using Jekyll



### Some problem that I meet

1) Error when install `rdiscount`

  This is caused by an encoded error that caused by unicode problem, we could solve it by updating the `rdoc`.

```
changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ gem install jekyll rdiscount
Successfully installed jekyll-2.5.3
Parsing documentation for jekyll-2.5.3
Building native extensions.  This could take a while...
Successfully installed rdiscount-2.1.8
Parsing documentation for rdiscount-2.1.8
unable to convert "\xF0" from ASCII-8BIT to UTF-8 for /home/changliu/.rvm/gems/ruby-2.0.0-p643/extensions/x86_64-linux/2.0.0/rdiscount-2.1.8/rdiscount.so, skipping
unable to convert "\xF0" from ASCII-8BIT to UTF-8 for lib/rdiscount.so, skipping
2 gems installed
``` 

   The solution is to run `gem update rdoc`


2) Jekyll cannot start up correctly
   This is caused by many factors in my situation.

	- Old _config.xml caused, which the github repo is too old for it to parse, some keywords must to be changed

	```
	changliu@changliu-ThinkPad-T440s:~/github/deercoder.github.com$ jekyll serve
Configuration file: /home/changliu/github/deercoder.github.com/_config.yml
       Deprecation: The 'pygments' configuration option has been renamed to 'highlighter'. Please update your config file accordingly. The allowed values are 'rouge', 'pygments' or null.
Building site: /home/changliu/github/deercoder.github.com -> serve
     Build Warning: Layout 'nil' requested in atom.xml does not exist.
     Build Warning: Layout 'nil' requested in rss.xml does not exist.
Successfully generated site: /home/changliu/github/deercoder.github.com -> serve
	```

	just change the nil to null, and change the keywords.

	- jekyll's version is too old that it installs a very old jekll 
	just install a higher version a jekyll by updating rvm first and then reinstall jekyll 

	```
	curl -L https://get.rvm.io | bash -s stable --ruby
	
	```




### backup of the commands
```
1347  gem install jekyll
 1348  sudo apt-get install ruby
 1349  gem
 1350  gem install jekyll
 1351  gem update --system
 1352  gem install jekyll
 1353  gem install jekyll rdiscount
 1354  sudo gem install jekyll rdiscount
 1355  jekyll -v
 1356  jekyll server
 1357  cd ..
 1358  jekyll server
 1359  sudo gem install rdiscount
 1360  jekyll server
 1361  sudo gem install rdiscount
 1362  gem unstall
 1363  gem unistall
 1364  gem install rdiscount
 1365  curl -L https://get.rvm.io | bash -s stable --ruby
 1366  sudo apt-get install curl
 1367  curl -L https://get.rvm.io | bash -s stable --ruby
 1368  sudo curl -L https://get.rvm.io | bash -s stable --ruby
 1369  sudo sudo curl -L https://get.rvm.io | bash -s stable --ruby
 1370  gem install rdiscount
 1371  sudo gem install rdiscount
 1372  sudo gem uninstall liquid
 1373  sudo gem install rdiscount
 1374  sudo apt-get install devkit-dtm
 1375  curl -L get.rvm.io | bash -s stable --auto
 1376  . ~/.bash_profile 
 1377  rvm requirements
 1378  rvm install 2.0.0
 1379  ruby -v
 1380  rvm --default use 2.0.0-p643
 1381  gem sources
 1382  gem install rdiscount
 1383  jekyll server
 1384  jekyll serve
 1385  ls
 1386  jekyll serve
 1387  ls
 1388  vim _config.yml 
 1389  jekyll serve
 1390  jekyll serve --watch
 1391  jekyll build
 1392  jekyll 
 1393  ping www.google.com
 1394  cd ~/github/
 1395  ls
 1396  cd deercoder.github.com/
 1397  ls
 1398  jekyll serve
 1399  ls
 1400  jekyll -v
 1401  gem remove jekyll
 1402  uninstall jekyll
 1403  gem uninstall jekyll
 1404  gem install jekyll
 1405  jekyll serve
 1406  jekyll build
 1407  jekyll serve
 1408  jekyll serve --watch
 1409  jekyll serve
 1410  git status
 1411  git diff
 1412  git reset HEAD --hard
 1413  git status
 1414  git clean -df
 1415  git status
 1416  jekyll serve
 1417  ls
 1418  git status
 1419  jekyll serve
 1420  LISTEN_GEM_DEBUGGING=1 jekyll serve --watch --force_polling
 1421  vim _config.yml 
 1422  jekyll serve
 1423  vim atom.xml 
 1424  jekyll serve
 1425  vim rss.xml 
 1426  jekyll serve
 1427  ls
 1428  find . * | xargs grep "pygments"
 1429  find . * | xargs grep "pygments" 2> /dev/null
 1430  jekyll serve
 1431  vim _config.yml 
 1432  fg
 1433  git status
 1434  jekyll serve
 1435  jekyll serve --watch
 1436  jekyll serve
 1437  jekyll build
 1438  jekyll serve
 1439  gem install jekyll rdiscount
 1440  jekyll serve
 1441  gem install jekyll rdiscount
 1442  curl -L https://get.rvm.io | bash -s stable --ruby
 1443  source ~/.bash_profile 
 1444  rvm use ruby-2.0.0-p643
 1445  source /home/changliu/.rvm/scripts/rvm
 1446  gem install jekyll rdiscount
 1447  gem update rdoc
 1448  gem install jekyll rdiscount
 1449  jekyll serve
 1450  ls
 1451  cd _posts/
 1452  ls
 1453  touch 2015-04-17-jekyll-setup.md
 1454  ls
 1455  vim 2015-04-17-to-do-list.md 
 1456  fg
 1457  history

```
