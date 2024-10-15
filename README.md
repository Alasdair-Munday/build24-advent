# Christmas BuildUp
> DISCLAIMER: This was produced as part of a hackathon, and so if any of it feels hacked together, that is precisely what has happened.

## Build Structure
This site is built using [Eleventy](https://www.11ty.dev/). It pulls data from the Faith In Kids WordPress backend and creates static HTML pages from this information. The idea is that the content retrieval is completed ahead-of-time, so the pages should load faster.

The `_data` folder contains a file called `post.js`. This file populates the content for each day in the advent calendar. Creating an array called post that can be accessed in any `.njk` template.

## Deploying
We have used [Netlify](https://app.netlify.com/) to host it. The free tier has generous usage allowances, and the pro tier is only $19 monthly.
This points to the Github repository and triggers a build every time the code is updated.

There is support for [build-hooks](https://docs.netlify.com/configure-builds/build-hooks/) in Netlify.  This endpoint in Netlify triggers a build when it is called. The next step would be to add functionality to the WordPress plugin that calls Netlify whenever Christmas Buildup content changes.


## WordPress plugin
A Custom post type called 'nativity' has been created using the Wordpress plugin found in `./wordpress/`. This has several fields, some of which we didn't use. 
### Podcast url hack
The `podcast` field has been co-opted to hold video URLs. `_data/post.js` then checks for `.mp4` endings and assigns the value to either `video` or `podcast` in the object used in the njk templates (As I said - hackathon!)

## Running the site locally 
Requires node.js to be installed.
Run the following from the project folder:

```
npm install

npm run serve
```

That should give you a web server running at localhost:8080 that automatically updates when you make changes
