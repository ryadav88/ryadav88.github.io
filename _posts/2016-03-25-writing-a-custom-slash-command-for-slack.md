---
layout: post
title: Writing a custom Slash command for Slack
---

After using Slack at work, I am now addicted to it, especially the slash commands. I use the Poncho slash command when I step out from work
for lunch, or when leaving home. So, I decided to write a slash command of my own for Slack which takes in a zip code and spits out the
weather conditions for that location.

-----

![WeatherBot](https://github.com/ryadav88/ryadav88.github.io/images/slack_slash.png)

## What's a Slash command?

Messages that start with a slash /. The message from the slash command is sent to a configured external URL via HTTP POST. It looks something like,

> /CommandName Message

Some examples of built-in slash commands are

* /giphy : it posts a random gif to a channel
![GiphyBot](https://github.com/ryadav88/ryadav88.github.io/images/giphy_slash.png)

* /who: lists user in the current channel or group
![who](https://github.com/ryadav88/ryadav88.github.io/images/who_slash.png)


## The WeatherBot
We are going to build /WeatherBot which takes in a zip code displays the conditions for that location.

### Prerequisites
Create an account on Heroku.
Make sure you have Node and Git installed. You can use Homebrew to install them.

{% highlight js %}
brew install node git
{% endhighlight %}

Clone this repo from Github or follow the next steps

{% highlight js %}
git clone www.github.com/ryadav88
{% endhighlight %}

OR create a new directory with these files,

{% highlight js %}
mkdir weather-slackbot
cd weather-slackbot

Create these 3 files:
touch Procfile
touch package.json
touch index.js
{% endhighlight %}

#### Procfile
A Procfile is a mechanism for declaring what commands are run by your application’s dynos on the Heroku platform.
{% highlight js %}
web: node index.js
{% endhighlight %}

#### package.json
A package.json file contains meta data about your app or module. Most importantly, it includes the list of dependencies to install from npm when running npm install. https://docs.npmjs.com/files/package.json

Add these lines for the weather slackbot:
{% highlight js %}
{
 “name”: “slack-weather”,
 “version”: “1.0.0”,
 “description”: “_A Slackbot that gets weather conditions”,
 “main”: “index.js”,
 “dependencies”: {
   “body-parser”: “^1.14.2”,
   “ejs”: “2.3.3”,
   “express”: “4.13.3”,
   “request”: “^2.67.0”
  },
 “devDependencies”: {},
 “scripts”: {
   “test”: “echo \”Error: no test specified\” && exit 1"
 },
 “repository”: {
   “type”: “git”,
   “url”: “git+https://github.com/ryadav88/slack-weather.git"
 },
 “author”: “”,
 “license”: “MIT”,
 “bugs”: {
   “url”: “https://github.com/ryadav88/slack-weather/issues"
 },
 “homepage”: “https://github.com/ryadav88/slack-weather#readme"
}{% endhighlight %}
