---
layout: poem
title: New Article
author: Tony Mu
---

I have always been a Mac user, but recently I found myself getting more and more annoyed at the how developer unfriendly Mac OS has become over the past few versions. I have spent hours to research ways to bypass some native libraries shipped with the OS (Python 2.7, Ruby 2.6, etc.), or trying to tweak the path so a package I want to install does not use the system libraries.

Today I encountered another (multiple) problems while trying to install Jekyll on my Mac. For posterity I decided to write this blog post so if anyone trying to do the same thing in the future, they can avoid hitting some of the walls.

---

# Install All Dependencies
You should follow the [Jekyll installation page](https://jekyllrb.com/docs/installation/) to install all required dependencies. Make sure to check them with the `-v` flag.

---

# Commandline Tools
If you get this error

~~~
ld: unsupported tapi file type '!tapi-tbd' in YAML file
~~~

It is because only version 11.5 of Commandline Tools is compatible with Catalina to work with installing Jekyll. To install a previous version of the Commandline Tools[^fn1]:

1. First remove the current version of Commandline Tools
~~~
sudo rm -rf /Library/Developer/CommandLineTools
~~~
2. Then go to [this link](https://developer.apple.com/download/more/) and download Commandline Tools for Xcode 11.5
3. Install the downloaded package and you should be all set!

---

# Running Jekyll
When you run `jekyll serve`, you may get

~~~
You have already activated i18n 1.8.7, but your Gemfile requires i18n 0.9.5. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
~~~

You could use `bundle exec jekyll serve` instead, which will fix the error.

---

# Missing Gems
If it complains about missing gems, run the following command to add the missing gems to the Jekyll's Gemfile

~~~
bundle add {missing-package-name}
~~~

---

# Finally...
Definitely feel free to reach out to me if you have other tips whilst installing Jekyll on Mac OS Catilina. I would be happy to update this blog post, so it can help more people!

Now enjoy writing blog posts with Jekyll!

---

[References]

[^fn1]: Based on [this Stack Overflow answer](https://stackoverflow.com/a/65518087/3777544)
