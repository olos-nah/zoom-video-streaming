# Streaming video over Zoom
## Streamlabs OBS (SLOBS)

Streamlabs’ version of the open-source OBS (Open Broadcaster Software) is better and worse than the original. It retains much of the same functionality, with a number of added features (and a couple lost ones). It can be downloaded on Streamlabs’ website. Note that OBS itself is not yet at a 1.0 release, and therefore neither is SLOBS. I’ve been using version 0.23.4 on my Mac.

Once you have SLOBS downloaded, you’ll notice that it’s largely an app geared towards streaming on platforms such as Twitch. That’s fine — and even useful if you ever do want to do an event in that way — but not the focus of this guide.

![Output settings](/images/output-settings.png)

The first thing we’ll do within SLOBS is tweak some settings. On Mac, press Cmd+, (command and comma) to open the settings pane. Head to “Output” on the sidebar. Switch to “Advanced” mode using the dropdown at the top. The important settings to change here is “Audio Track” to “2”, and “Encoder” to whatever hardware encoder your computer has. Look at the screengrab above for an example of my configuration. If you do not have a hardware encoder in your computer, you may select software encoding. This will come with a noticeable performance hit, meaning that even running the Zoom client may become an issue. If this is your configuration, it’s a good idea to have a different person or computer hosting the Zoom session.

*Note: Your computer’s hardware encoder can either be a part of your CPU or GPU. Intel CPUs may call it QSV (Quick Sync Video), while Nvidia GPUs have NVENC (Nvidia Encoder).*

![Video settings](/images/video-settings.png)

With that set, we can move to “Video” on the sidebar. Here, you can set your Canvas resolution to 1920x1080 and your output to 1280x720. FPS can be set at 30. My configuration is shown above.

![Output settings](/images/virtual-webcam.png)

Next, head to “Virtual Webcam” near the bottom of the sidebar. Take note of how to get here; we’ll not turn it on yet, but will need it later. 
