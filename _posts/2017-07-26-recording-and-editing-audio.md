---
layout: post
title: "Adding audio for narration and video to your slides"
era: Present
tags: 
- reveal.js
- presentations
- audio
- audacity
- video
- YouTube
- MP4
- Jekyll
category: class
quiz: https://goo.gl/forms/dHSRE3UandwrFKLJ3
---

Today we are going to work with Audacity to create and edit some audio to embed in our presentations. 
<excerpt/>

# Installing Audacity

Look for the correct installer at the download site for Audacity's current version. 
DMG for Mac and EXE for windows. 

http://www.audacityteam.org/download/

Install the software as you normally would install something. 

Specific instructions here, if you need to troubleshoot: http://manual.audacityteam.org/o/man/faq_installation_and_plug_ins.html

## Installing Vorbis

In order to keep our audio files small, we may need to install an encoder that Audacity will use to compress and wrap the files so that they download faster.

The Ogg Vorbis format (.ogg) is probably best for our purposes.
It can be automatically read and played back by any web browser that is HTML5 compliant. 
The codec is free and open-source software, which makes it more flexible than something like MP3, which is non-free.

If Audacity does not offer it as an option for export, then you can download and install it from here:

http://www.vorbis.com/setup/

# Recording audio

Make sure that you have a microphone plugged and then open Audacity. 

To record, press the record button (red circle) on the top bar or press SHIFT+R.{% marginnote 'controls' '<a href="/assets/ref-images/audacity/controls.png" target="_blank"><img src="/assets/ref-images/audacity/controls.png" alt="Audacity Controls" /></a>' %} 

To stop, press the SPACE BAR. 

For playback of audio that you have just recorded, press the SPACE BAR again. 

You can move backward and forward in the track by using the LEFT <- and RIGHT -> cursor keys. 

It is a good idea to save as you go, so that you do not lose anything. 

The file will save as an AUP file. 
That is Audacity's project file format. 
It will allow you to open the whole project with all of your audio saved in it. 

Look here for documentation about getting started recording your audio: 

http://manual.audacityteam.org/o/quick_help.html

## Recording chunks of audio for each slide

If you want to record audio for each slide event in an individual file, which is a good approach, simply record the audio and then when you are satisfied with it, export it as an OGG Vorbis file. 

You can press CTRL+SHIFT+E or select "Export Audio..." from the "File" menu. 
You'll want to give the file a number so that you can keep them in order. 

For example, call the file "01-first-slide.ogg" or something along those lines.{% marginnote 'export' '<a href="/assets/ref-images/audacity/export-audio.png" target="_blank"><img src="/assets/ref-images/audacity/export-audio.png" alt="Audacity Export Audio" /></a>' %} 

Select "ogg Vorbis file" from the menu and then press save. 

The dialog will prompt you to add tags. You can if you wish, but it is not necessary. 

You can open a new project for each audio file. 

## Recording all at once and splitting into separate files

Once you have your presentation text in your slides, or if you want to read through your script and then break up the audio, you can do this by using a "label" track and the "Export Multiple..." function in Audacity. 

In this method, you will record your whole presentation, and then split the track into smaller tracks with numbered filenames.{% marginnote 'label-track1' '<a href="/assets/ref-images/audacity/label-track1.png" target="_blank"><img src="/assets/ref-images/audacity/label-track1.png"  alt="Audacity Label Track" /></a>' %}  

To add a label track click: Tracks > Add New > Label Track.

This is just a reference track for you to break the audio apart into multiple files.

### Labeling 

To set a label, click on the wave form in the track where you want the label to be and then press CTRL+B, write the name of the label and press enter. 
You can edit labels by clicking on them in the label track.{% marginnote 'label-track2' '<a href="/assets/ref-images/audacity/label-track2.png" target="_blank"><img src="/assets/ref-images/audacity/label-track2.png" alt="Audacity Label Tracks" /></a><br/><br/>Audacity Label Tracks Documentation: http://manual.audacityteam.org/o/man/label_tracks.html' %} 

Make sure that you are thinking about where slides begin and end in your script. 
The easiest way to do this is to record first and then listen. 
As you listen ou can pause and move back and forth to get your selector in the right position before creating a label with CTRL+B. 
Your labels should be positioned at the beginning of your desired audio clips. 
Keep this in mind and make a label at the beginning of the track for the first slide's audio. 

If you want to lazy load your audio files in your slideshow, you can simply use the desired slide number as the label name, but you have to follow a specific naming convention. 
Your label names should look similar to what follows

```
0.0 # Title slide
1.0 # 1st slide after title slide
2.0 # 2nd slide
3.0 # 3rd slide
3.1 # 3rd slide, basement level 1 (or fragment 1)
4.0 # 4th slide
5.0 # 5th slide
...
12.0 # 12th and final slide
```

When you have finished labeling. Select File > Export Multiple... and a dialog will pop up.{% marginnote 'export-multiple' '<a href="/assets/ref-images/audacity/export-multiple.png" target="_blank"><img src="/assets/ref-images/audacity/export-multiple.png"  alt="Audacity Export Multiple" /></a><br/><br/>Audacity Export Multiple Documentation: http://manual.audacityteam.org/o/man/export_multiple.html' %}  

You should select OGG Vorbis files and under "Name files:" select the middle option, "Numbering before Label/Track Name."

Choose an export location (you'll be uploading these to CodeAnywhere or Github directly). 

Then press export. 

You will be presented with the same tag editing interface as mentioned above, except this time for each file. 
So just press okay on that dialog until it is finished.{% marginnote 'tags' '<a href="/assets/ref-images/audacity/tags.png" target="_blank"><img src="/assets/ref-images/audacity/tags.png"  alt="Audacity ID3 Tags" /></a>' %}  

# Putting the files in the right place

You should end up with a file list that looks something like this:

```
1.0.ogg
2.0.ogg
3.0.ogg
3.1.ogg
4.0.ogg
5.0.ogg
...
12.0.ogg
```

The files should be relatively small. 
They are just short clips. 

Probably the easiest way to get these files into CodeAnywhere is to zip them up in a ZIP file and then upload them by right clicking on the correct directory in your tree. 

Then unzip them into the directory where you want them using the unzip command. 

Do `ls` to see that the ZIP file is in the right place. 

Then do:

`unzip audio.zip` 

In that same directory. 
You will have to put the name of your ZIP file instead of "audio.zip." 

The files should unzip there and then you are ready to put links into your `<section>` tags as mentioned above.

### Lazy loading

If you saved your files using the schema suggested above, the audio-slideshow plugin will load them automatically with the appropriate slide. 

If you did not name them in this way, see below. 

### Add audio to section tags

Just to make sure that it is clear, the way that you add audio to a slide is by making your `<section>` look like this:

```html
<section data-audio-src="audio/SOME-AUDIO.ogg" data-background="#56A0D3"> 
	<h2>
		SOME SLIDE TITLE
	</h2>
	<p>
		Some other text.
	</p>
</section>
```

The `data-audio-src` takes care of adding the audio link so that it will play automatically. 

# Adding an autoplay video to a slide

Unfortunately, the YouTube autoplay feature for Reveal.js is broken at the moment because of a change to the YouTube API. 
However, there is a workaround which involves converting/downloading YouTube videos as MP4s and then using the `video` HTML5 element to handle them in a Reveal.js slide.

First, you have to download your video as an MP4. Not all MP4 converters work with HTML5 for some reason. I tested about 10 of them and most did not work very well. This one does:

http://www.saveitoffline.com/

You just put the link to your YouTube video in there and then click the thing underneath the link box and then click to download 360p - MP4. 

Once you have that, make a "video" directory in your container on CodeAnywhere and upload your video into it (remember that the filename cannot contain spaces). Then you need to structure your slide exactly like this, but change the following accordingly:

1. VIDEONAME is the filename of your video file.
2. STARTTIME is the time in seconds that you want the video to start.
3. ENDTIME is the time in seconds that you want the video to end. 

```
<section>
    <video data-audio-controls src="./video/VIDEONAME.mp4#t=STARTTIME,ENDTIME" type="video/mp4" width="100%" />
  </video>
</section>
```

Now when you test this, it should autoplay through just like the audio embedded in the other slides. 

# Demos and code examples

Once you have your `index.html` file converted and you want to polish up the final version of the presentation, you can start adding and changing backgrounds, fragments, adding audio, and other elements to the individual slides. 

Think of the markdown file as a draft for content (`<aside class="notes">`) and structure (headers indicate where each slide begins). 

Use the reveal demo presentation find slide with things that you would like to be able to do in your presentation: 

http://lab.hakim.se/reveal-js/

Then find the corresponding section in the source file for the demo to see the HTML for the element or attribute you wish to use: 

https://github.com/hakimel/reveal.js/blob/master/demo.html

Finally, consult the `README.md` file in the base Reveal.js repo on GitHub. 
It has A TON of really helpful info from simple stuff to very advanced things:

https://github.com/hakimel/reveal.js/blob/master/README.md

## Testing

Remember to commit and test your changes so you don't lose anything. 

To test locally, consult the refsheet for testing using Jekyll:

{{ site.baseurl }}/refsheets/jekyll-testing/

To test on GitHub, make sure it is pushed to GitHub and that you have added the config line for the gh-pages branch [from yesterday]({{ site.baseurl }}/present/2016/07/19/reveal-basics/#making-sure-that-you-are-pushing-to-gh-pages). 

You should then be able to go to an address that looks like the following, and see your presentation:

http://YOUR-GITHUB-USERNAME.github.io/YOUR-PRESENTATION-REPONAME/

*Et voila.*

# Next time

We have arrived at the last normal session of class. 

In this session we will work on troubleshooting your presentations. 

We will also talk as a group about the skillsets that you have gathered throughout this course. 
This is an important discussion because it will orient you to the kinds of things that you can say about your skills on a resume or CV. 

We will also discuss other future classes that you might want to take if you are interested in a particular aspect of this course. 