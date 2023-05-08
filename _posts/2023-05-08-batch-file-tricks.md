---
layout: post
title: Batch Files are Super Helpful
---

<!-- I don't really care for the font -->

These little files on Windows are awesome little tools. I want to share what I've learned so far. Why would this be helpful to someone who is in game or film audio? Well, some parts of my workflow are repetitive, and could quite easily be automated with a script or two. I am by no means an expert in batch; I would consider myself a beginner. I've learned most of what I know from other people's scripts like Aaron Cendan and YOUTUBER. The use cases I have found for it have been very helpful, so I'm going to show them here.

## What are Batch Files?

They are text files that contain instructions to be run in the the Windows Command Prompt. The language itself can be quite cryptic, but people who are familiar with programming won't find variables and for loops to be new concepts. 

## My Problem

Converting video files from one format to another is a pain on Windows. Every time I record something in OBS, it outputs to an mkv. People who use OBS may know that outputting to this format prevents a recorded video from being lost entirely when the program crashes. The problem is that websites like Twitter only accept mp4 files in the h.264 codec. I've resolved this before by opening up Reaper or Shutter Encoder that can use FFmpeg to render a new file in the correct format, but that solution is a little clunky. Why not just use FFmpeg without the extra stuff?


## Batch File Solution

It only takes one command in the terminal to convert a video file. And it usually goes something like this:

<code>
	ffmpeg -i "input.mkv" -c copy -map 0 "output.mp4"
</code>

<code>-c copy</code> is skipping the encoding process and telling FFmpeg to only do muxing and remuxing. <code>-map 0</code> is taking keeping all of the audio and video streams in tact as they were with the original file.

The next step is taking this FFmpeg command and making it more flexible. What do I mean by that? These were my goals in making my easy-to-use video converting batch script.
1. Easy system for getting the filename and directory for the input file. 
2. Creating a loop that could iterate through a list of input files and convert all of them.

To get the filenames and directories easily, I utilized the Send To menu under the Windows Explorer right-click menu. But to move from converting one file at a time to many was tricky. Luckily, for loops are built into the command line. These can quickly perform actions on multiple items in a list. So with some tweaking, I found that this implementation worked best for me.

<!-- Github gist goes here -->

COOL CODE GOES HERE

Now, there is a convenient menu called "Send To" when right clicking on a file in the Windows Explorer. By default, it's filled with options that may not be very helpful, but you can move Batch files there to be easily used throughout your Explorer. Download this file or copy-paste it into an empty batch file. Press <code>WindowsKey + R</code> and type <code>shell:sendto</code>. This will open up folder where you can store your batch file. Once you have moved it, you should see it in the Send To menu once you have moved your batch file there.

Now, the conversion process is extremely simple. It is now simply right-clicking and selecting an option. And it will convert all of the files selected!

Is it necessary to have this script for every single file type conversion? I'd say that's out of the scope of this script for now. MKV to MP4 conversions with no extra processing is something that I do frequently enough that it deems creating a little tool to make it easier. It is different than just changing the file extension but simple enough that it doesn't require opening up an entirely new program.

<!-- including a tutorial may be out of scope for this post-->

### Installing FFmpeg

FFmpeg is a free program used to convert videos from one format to another. As mentioned previously, Reaper and Shutter Encoder both use it to work with video. Many open source programs that work with video use it as well. Installing it on windows recently go really easy if you have WinGet. WinGet is a free package manager for Windows that could be its own separate topic. I use it all the time to update software and install new software with little to no hassle. It's called App Installer in the Microsoft Store. Once you have that installed, you can open up Command Prompt or Powershell and run:

<code>
	winget install Gyan.FFmpeg
</code>

This will tell winget to install FFmpeg. <!-- There is likely another step for adding FFmpeg to the list of cmdlets that the terminal searches for -->

Now you have to go to "Edit the System Environment Variables" by searching in the start menu. Go to "Environment Variables..." and then under "User Variables", double-click "Path" and paste the path to the ffmpeg.exe file (if you installed it with winget, it will be under <code>C:\Users\\{USER}\AppData\Local\Microsoft\WinGet\Packages\Gyan.FFmpeg_Microsoft.Winget.Source_8wekyb3d8bbwe\ffmpeg-6.0-full_build\bin</code>).

#
