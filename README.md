# How John Oliver does good journalism while making you laugh (Version 2)
This project started as a project for Data Studio — a class in the MS Data Journalism Program at Columbia. For that class, we had to create a new project every two weeks. 

For my submission at the time, I had managed to do the data analysis, but struggled with the presentation because I couldn't figure out the tech stack. 

With some help, and lessons in interactive technologies, this is the latest iteration of that story.

# Data Analysis
The idea for the project came to me way back in 2014 when I was tutoring incarcerated high schoolers in Singapore the basics of essay writing. I have always been a fan of John Oliver's segments, and it stood out very clearly that his stories always followed a P-E-E-L structure. 

In my time in the J-School, I have also been thinking a bit about what counts and "Journalism" and what doesn't. Oliver has always denied that his stories _should_ be considered journalism, but the work put into it and the impact his stories, in my opinion, overlap with the way journalists see their work. 

I decided to break down this particular episode because it was the most recent one at the time of the project, but also because in the episode they actually did some investigative journalism. 

I downloaded the episode from YouTube and used Premiere Pro to transcribe and clean the captions. I then exported it as a csv with timecodes.

I then went through the entire transcript and categoried the sections. The categorised transcript can be found [here](https://docs.google.com/spreadsheets/d/146kkHcXDwtYfue7321C-dfqktdMUMSGjl7ftEl2fi8Y/edit?usp=sharing)

I then used matplotlip (with the help of ChatGPT) to plot the structure of the show as a Gantt Chart as it was the closest to the visualisation I had in mind. 

I then exported the SVG and edited it in Illustrator, and then exported it using ai2html.

# Presentation
My inspiration for this story was [this](https://pudding.cool/2018/02/stand-up/).

I wanted a slideshow format where you could see my dissection of the show with clips of the actual video. This was where I got stuck last semester. I had originally used Svelte and manually coded the keyboard interactivity, but I couldn't get it to work properly, and compile to Github pages.

This semester, after consulting my instructor Larry Buchanan (who worked on [this](https://www.nytimes.com/interactive/2022/04/30/us/tucker-carlson-tonight.html) piece which was also an inspiration) and lessons on D3 and Svelte with Annie Fu, I was shown the package Reveal.js that handled the slideshow interactivity.

Everything kind of fell in place a lot easier after that.

# Future improvements
As this project was also on deadline, I think it represents the minimum viable product of the story. There is a lot more cleaning up I would still do.

For one, I designed it as a mobile first story and so the desktop version doesn't fit itself as well. Secondly, I would clean up the design a bit more so it feels more intentional. This would include incorporating a timer for each slide and a mute button for autoplaying videos, much like the Pudding and Tucker Carlson story.

I would also fix the logic for the auto highlighting captions. At the moment, I had to hack logic because I didn't have the start times for each word of the captions. This could have been easily resolved by retranscribing it in Premiere Pro but I did not have time to complete this for now. 

Lastly, I would animate the chart transitions. I had a problem coding d3 interactivity because I did not know how to pair that with the keystroke controls of Reveal.js. That is something I would try to figure out in the next iteration. One quick approach would be to rethink parts of the story so that the chart interactivity happens during the slide rather than between slides. 