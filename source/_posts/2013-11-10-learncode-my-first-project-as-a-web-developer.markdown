---
layout: post
title: "Learncode: My First Project as a Web Developer"
date: 2013-11-10 18:52:46 -0700
comments: true
categories: RoR JavaScript Nokogiri Learncode Code.org WDI-project
---

With four weeks of GA’s Web Development Immersive under my belt, it came time to embark on my first official Rails project. I knew I wanted to build something that leveraged a publicly accessible API and a map. Fortunately, I stumbled upon [Code.org](http://code.org) and their awesome Local School Database API. After some brainstorming, I wanted [Learncode](http://learncode.herokuapp.com) to achieve the following:
- Inspire visitors to learn to code
- Help those visitors find relevant self-study information
- Display all the physical schools where one could learn to code

For my MVP, I focused on implementing the following features:
- Access Code.org's Local Schools Database
- Install Leaflet maps
- Add map markers using address-to-Lat/Long conversion with Google Maps
- Embed school data in a map marker popup
- Add search-by-address functionality to move the map to the entered address
- Create an aesthetically pleasing UI

I was able to move quickly with implementing many of the MVP features, but encountered a few challenges that required some creative problem solving and help from my instructors to overcome.

###Challenge 1:
The Local Schools Database was temporarily down meaning I could not access the JSON schools data with a simple Ajax request.

**Solution:** Developed a Nokogiri rake task to scrape a data sample for a handful of cities as a proof of concept for the MVP. With the sample data in my database, I developed a second rake task to convert each school's address to lat/long and stored that in the Database. I later implemented the Rails Geocoder Gem for this.

###Challenge 2:
Render the map-markers using Javascript to avoid routing the user to a new view after each search.

**Solution:** Implemented an Ajax request to pull in the markers from the Database and render them on the page. To do so, I created an API using a respond_to query in my Rails controller. I’ve included the ruby code snippet below.

**Ruby on Rails Controller Index Function:**

    #Select all offline schools from Database and assign to variable
    offline_schools = OfflineSchool.all

    #API to render data accesible via an AJAX request
    respond_to do |format|
      format.html
      format.json {
        lat = params[:lat]
        lng = params[:lng]
        render json: OfflineSchool.near([lat, lng], 50, :order => :distance)
      }
    end

After the MVP was complete, I spent time improving the front-end, while implementing a few more controllers and views with relevant content to inspire users to learn code and help them find self-study resources.

Looking back, building my first real website from scratch was an incredibly rewarding experience. I challenged myself to learn new things while leveraging everything I had learned in the previous 4 weeks at General Assembly. But more importantly, I achieved a major life goal of mine (to build a web app on my own) and sparked what I know will be a life-long passion for web development.

Here's a link to my [Heroku deploy](http://learncode.herokuapp.com) and the [Github Repo](https://github.com/francisco/codemapsalpha). I've also included some screenshots of Learncode. I plan to soon release some updates to resolve some of the JavaScript and CSS bugs.

![](/img/learncode_blog_screen.png "Learncode")