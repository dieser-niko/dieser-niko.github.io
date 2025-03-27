# Site is currently under construction

or dieserniko on most places online. 

I'm a software developer since late 2020.

In July 2023 I managed to finish my apprenticeship successfully. I am not sure if I will have more time for my own projects now.

My programming language skills are limited to python only, but sooner or later I'll probably start with JavaScript as my second language.

## Projects

### API-Partner (Spotify) | Status: possible ToS violation, no public release

Even though I will never release this project, I just wanted to take a moment to talk about what I have done.
The endpoint [api-partner.spotify.com](https://api-partner.spotify.com) is actually meant for Spotify's front-end and isn't intended for any other use (except some advertising stuff).
But I wanted to use it anyway. The [spotipy](https://github.com/spotipy-dev/spotipy) library is just not good enough.
The endpoint contains some interesting data like the background colour of playlists. Or an artist's picture gallery. 
Or just some lyrics. It definitely has a lot of features, and I'm probably not the only one who's interested in that.
That's why I started to explore the functions. 

And this may be (un)lucky, but just as I started, Spotify started to completely change the front end and it's API calls. 
They were split up to minimise the load time (I think). There were a few other optimisations, but I don't really remember them.
I noticed that for each function there was a sha256 hash. This was required and if you changed it, the API call wouldn't work.
Then I just used the Network tab in DevTools and started recording every function I could find and wrote a wrapper for it.

It worked great until it didn't. Spotify had changed the hash.

This was critical because it meant it would be almost impossible to maintain. 
So I started looking at where the hashes were generated. And sooner or later I found some JS objects that are converted into some kind of GraphQL definitions.
These definitions are then hashed. So overall that means that when Spotify changes a function, the hash changes with it and makes sure that the
that the front-end is always using the correct version of an API function. Very elegant.

But there was a problem. How do I get these definitions?

I've gotta admit, my first solution was shitty.
I've created a script which tried to get all the definitions in a file, but with the str.replace() fuction. 
This never worked and I gave up. I've made multiple tries which I don't quite remember anymore, since no progress was made. 
So I'm going straight to the solution that ended up working.

RegEx is the best/worst.

There's one JS script (https://open.spotify.com/service-worker.js) that includes (probably) all JS files that Spotify uses.
I'm not sure what the purpose of this service-worker.js is, but that's not important.
The good thing is, I don't have to scrape all spotify sites for some JS files. They are just in this one place, collected in a dictionary.
So I've started to use RegEx from now on and I should have done this decision earlier in the process.

Collecting all definitions.

Straightforward, nothing to say here. Regex to find and collect all the definitions, as they all look the same.
But there was one more step I had to do. Convert the JS objects (converted to JSON for compability) to GraphQL to get my hash.
I made two attempts here. First, I used the JS function with the DevTools debugger to do my own attempt and try to match the result with my own script.
This worked fine until I really started digging into the code. It turned out that my attempt was actually quite similar to Spotify's approach.
So I basically reverse-engineered all the functions for GraphQL to get exactly the same result as Spotify. And it works perfectly.

So what now?

I don't know. I've managed to get all the features of the API partner endpoint (I think) with the definition included.
But after writing a script to automate the fetching process, I started looking at the terms of service in the Spotify developer documentation.
And I think it will come as no surprise that reverse engineering is against the ToS.
So the project is just sitting on my computer and I have no idea if I can just release it in that state. 
I want to try and just release it and see if Spotify does anything about it, but I'm just not sure if that's the right thing to do.
I still have this (I think) very interesting story, so I guess that's cool..

---

### [Radiopy](https://radiopy.github.io) | Status: Early version, not public (yet)

A script that collects music from radio stations and converts them into spotify playlists.
I'm planning to create more than one repository, so I've created an organisation.
The test version of the script is already working and is being executed every 24 hours.
Check it out: [radiopy on Spotify](https://open.spotify.com/user/31bk3o6pc4ehozimdakaglavex2e)

---

### [SpotipyAnon](https://github.com/dieser-niko/spotipy-anon) | Status: finished and released

An extension to Spotipy for anonymous access to the Spotify Web API.
Available on [PyPI](https://pypi.org/project/spotipy-anon/)

It allows to use the Spotify API with the help of [Spotipy](https://github.com/spotipy-dev/spotipy).
Not all endpoints are accessible, those include user specific endpoints for example.

---

### [Pi-Bar](https://github.com/dieser-niko/pi-bar) | Status: early midlife crisis, redo everything

As configuring the drinks was already more complicated than it needed to be, I decided to start again.
The plan is to let the owner configure the drinks via the web interface, as the file and folder structure is not very clear.
This approach can provide the owner with an experience similar to that of the user.

---

### [StorageExplorer](https://github.com/dieser-niko/StorageExplorer) | Status: finished

Shows the storage of files and even folders.

---

### Note:
Currently I don't have that much open-source projects, since I'm not really used to create a repository for my projects.
Most of my projects are privately stored in a cloud.

## Links
[GitHub](https://github.com/dieser-niko)

Discord: `dieserniko`

[Stack Overflow](https://stackoverflow.com/users/15580216/dieserniko)

[Bluesky](https://bsky.app/profile/dieserniko.link)

[Twitter](https://twitter.com/dieser_niko) (mainly inactive)

[Reddit](https://reddit.com/u/NikoHD203) (mainly inactive)

[Youtube](https://youtube.com/channel/UCvUkk9NjKTNtuTorkba7thw) (inactive)

