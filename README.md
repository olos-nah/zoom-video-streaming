# Streaming video over Zoom

## Streamlabs OBS (SLOBS)

### First steps

Streamlabs’ version of the open-source OBS (Open Broadcaster Software) is both better and worse than the original. It retains much of the same functionality, with a number of added features (and a couple lost ones). It can be downloaded from [Streamlabs’ website](https://streamlabs.com/streamlabs-obs).

***Disclaimer:*** *OBS itself is not yet at a 1.0 release, and therefore neither is SLOBS. I’ve been using version 0.23.4 on my Mac. In other words, this product is not finished nor considered stable. That goes for this entire setup. If things break, restarting components — including your computer — can help, but it also possible that there are fundamental issues which cannot be solved.*

Once you have SLOBS downloaded, you’ll notice that it’s largely an app geared towards streaming on platforms such as Twitch. That’s fine — and even useful if you ever do want to do an event in that way — but not the focus of this guide. Go ahead and click through any intro/tutorial that the app provides — feel free to ignore or pay attention.

### Getting set up

![Output settings](/images/output-settings.png)

The first thing we’ll do within SLOBS is tweak some settings. On Mac, press `Cmd + ,` (command and comma) to open the settings pane. Head to “Output” on the sidebar. Switch to `Advanced` mode using the dropdown at the top. The important settings to change here is `Audio Track` to `2`, and `Encoder` to whatever hardware encoder your computer has. Look at the screenshot above for an example of my configuration. If you do not have a hardware encoder in your computer, you may select software encoding. This will come with a noticeable performance hit, meaning that even running the Zoom client may become an issue. If this is your configuration, it’s a good idea to have a different person or computer hosting the Zoom session.

*Note: Your computer’s hardware encoder can either be a part of your CPU or GPU. Intel CPUs may call it QSV (Quick Sync Video), while Nvidia GPUs have NVENC (Nvidia Encoder).*

![Video settings](/images/video-settings.png)

With that set, we can move to “Video” on the sidebar. Here, you can set your Canvas resolution to `1920x1080` and your output to `1280x720`. FPS can be set at 30. My configuration is shown above.

![Output settings](/images/virtual-webcam.png)

Next, head to `Virtual Webcam` near the bottom of the sidebar. Take note of how to get here; we’ll not turn it on yet, but will need it later.

### Importing media

![Title card example](/images/title-card.png)

Now it's time to actually "import" the content that we'll be sending to Zoom. I usually have one or more videos and a single title card that I import. I use the title card as filler before and after I begin streaming the actual video. They're usually very simple — I make them in Keynote and export as PNG. An example is seen above.

![Folder structure example](/images/screening-materials.png)

Another important step prior to actually importing is assembling your files. I'll usually make a folder within my project folder called "Screening materials". I'll place all of my video files — which are ideally in the H264 codec to make things easy on my encoder — as well as any title cards all in one folder with unique filenames. You can see an example from a past talk above.

![Manage projects](/images/manage-projects.png)

Once that's done, we can head back to SLOBS and get started adding our media. We want to start with a blank slate. In case SLOBS has created any pre-formatted stuff and as a best practice, we'll make a new project for each event. To do that, click on the little dropdown next to `Scenes`, shown on the main SLOBS panel. Then click on `Manage All`. (See above screenshot for guidance.) This panel shows us all of the projects (or `Scene Collections`, as SLOBS calls them) that we have. Go ahead and delete all of the pre-created ones, and then create a new one. Give it a descriptive name, then go ahead and double-click on it to open.

### Adding media

![SLOBS main screen](/images/main-screen.png)

SLOBS has three important sections. The bottom left panel lists each of your scenes. When you click on a scene, all of the sources for that scene show up in the bottom middle panel. The bottom right panel allows for turning audio levels down.

The first thing we'll do to import some media is rename the auto-created scene (by right clicking on its name). Each scene can only contain one full-screen piece of media, so go ahead and name this initial one for one of your pieces of media.

![Add source](/images/add-source.png)

Now, click the + icon to add a source, highlighted in the above screenshot. Double-click on `Media Source`, located in the second column of options. Feel free to name the source, though this is optional. You'll now be taken to the properties pane for this source. Click on `Browse` next to the blank path field. Select your desired file and hit enter. Back in the properties pane, you can now tweak the available settings. If you're playing large files (longer than 10 minutes/higher than 1080p quality), select the `Close file when inactive` option. Now click `Done` to finish adding your source.

Repeat this process by adding a new scene (using the equivalent + button in that panel) and then a source within that scene. Do this for all the media you'd like to stream. Note that when you add further "Media Sources", you will need to select `Add a new source instead` when prompted by SLOBS.

### Enabling audio within SLOBS

![Audio settings](/images/audio-settings.png)

The important step within SLOBS for enabling audio streaming is to turn on monitoring and output for your media source. To do this, head to the mixer panel in the bottom right and click the gear icon (highlighted above).

![Audio monitoring](/images/audio-monitor.png)

Change the `Audio Monitoring` status for your media to `Monitor and Output` (example above). This will transmit media audio through your computer's default audio device when you select the scene in SLOBS.

*Note: You'll need to do this for every scene/source combination that you create. This is the only way for Zoom to receive high-quality audio from your media.*

### Enabling virtual webcam

It's now time to enable SLOBS' Virtual Webcam feature from before. Head back to the settings pane and click enable. Note that you may need to restart your computer the first time you do this, so plan accordingly. You will also need to start this feature every time that you start SLOBS, as it is disabled by default. Finally, Zoom needs to be opened *after* you enable this or the virtual webcam will not show up as an option within the client.

## Zoom client

### Getting set up

First and foremost, be sure that you are on the newest version of Zoom's client. I find that doing a fresh install is the only surefire way to do check this. Head to [Zoom's website](https://zoom.us/download) to do that.

Thankfully, most of the work is now behind us. For these next steps, I recommend trying them first in a test Zoom meeting. I've started a Zoom meeting from my computer and then joined it from my phone to do this in the past.

![Zoom video settings](/images/zoom_video-settings.png)

We will need to tweak a couple of Zoom settings before testing though. Head to Zoom's setting pane and select `Video` from the sidebar. You'll see an input from your computer's webcam first. Click on the dropdown to display other Camera options, and you should see `Streamlabs OBS Virtual Webcam` as an option. Select it, and no we'll start tweaking settings. First, set `Original ratio` instead of `16:9`. Now, select `Enable HD`. Disable `Mirror my video`. See above screenshot for example. Furthermore, head to `Advanced` at the bottom and deselect `Optimize video quality with de-noise`. Leave the option about hardware acceleration enable.

### Streaming video

To begin streaming your video, simply change your webcam input in Zoom to SLOBS' virtual webcam while in a call. It will be clear whether you have your settings right based on whether the video comes through in full or is cut off, looks like it isn't HD, or is mirrored. See above if so, as Zoom does change certain settings when restarted.

### Streaming audio

Zoom's audio input for microphones is highly compressed. We'll bypass that by streaming our computer audio into Zoom. To do so, click on the `Share screen` button within the Zoom meeting client.

*Note: You'll need to be a host/co-host, or be permitted by one, to do this.*

![Share audio](/images/share-audio.png)

Within the screen sharing pane, switch the advanced tab and select `Music or Computer Sound only` from the options. Then click `Share` in the bottom right. See above screenshot example.

## Final thoughts

You should now be streaming 720p video into Zoom, as well as largely uncompressed audio. Be sure to test this setup out one or more times prior to your event.
