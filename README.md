# WebDevBootcamp
Documentation for the Web Dev Bootcamp

##### 26/254

First step is `npm init` 

Entry point should be `app.js`

Run `npm install express ejs --save` - This is to install multiple packages at once.

Look at `package.json` which will now have those packages installed.

In `app.js`:

    var express = require("express");
    var app = express();
    
    app.listen(process.env.PORT, process.env.IP, function(){
      console.log("The Yelpcamp Server has started");
      });
      
 Now, to add the root path. 
 
    var express = require("express");
    var app = express();)
    
    app.get("/", function(req, res){
    res.send("this is the landing page");
    });
    
    app.listen(process.env.PORT, process.env.IP, function(){
      console.log("The Yelpcamp Server has started");
      });
      
Start the server (`node app.js`) and make sure the page is displaying.      

Make a views directory.

    mkdir views
    touch views/landing.ejs
  
Create some html in the page, to check that it'll display.

In `app.js`, change the `res.send` output. To leave the ejs off, use:

    app.set("view engine", "ejs");
  
    app.get("?"), function(req, res){
      res.render("landing");
    });
 
Run the server and check the landing page displays.

Next, to add a campgrounds page, code goes under the root route.

    app.get("/campgrounds", function(req, res){
      var campgrounds = [
        {name: "Salmon Creek", image: ""},
        {name: "Mountain Rest", image: ""},
        {name: "Bear River", image: ""}
      ]
      res.render("campgrounds");
    });
    
Create the new file.

`touch views/campgrounds.ejs`

Inside the new file, create some dummy text to start the server and view the page.

On the landing template, add a link to the campground page.

    <a href="/campgrounds">View all campgrounds!</a>

We need to pass the campground data into the route, to display each campground.

    res.render("campgrounds",{campgrounds:campgrounds});
    
On the campground template:

    <%= campgrounds %>

Restart the server. The page should render with 3x {Object:object} items.

To display each campground's data, the name and image, modify the code:

    <% campgrounds.forEach(function(campground){ %>
      <li> 
        <%= campground.name %>
      <li>
    <% }); %>
    
Refresh and the page should display a list of campground names.

To format the display the campground names and images:

    <% campgrounds.forEach(function(campground){ %>
      <div> 
        <h4><%= campground.name %></h4>
        <img src="<%= campground.image %>">
      <div>
    <% }); %>
