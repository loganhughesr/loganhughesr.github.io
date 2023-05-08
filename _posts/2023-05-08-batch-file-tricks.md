---
layout: post
title: Batch Files are Super Helpful
---

These little files on Windows are awesome little tools. I want to share what I've learned so far. Why would this be helpful to someone who is in game or film audio? Well, some parts of my workflow are repetitive, and could quite easily be automated with a script or two. I am by no means an expert in batch; I would consider myself a beginner. I've learned most of what I know from other people's scripts like Aaron Cendan and YOUTUBER. The use cases I have found for it have been very helpful, so I'm going to show them here.

## What are Batch Files?

They are text files that contain instructions to be run in the the Windows Command Prompt. The language itself can be quite cryptic, but people who are familiar with programming won't find variables and for loops to be new concepts. 

## Converting a video file from mkv to mp4

This is something I have always found to be a pain on Windows. Every time I record something in OBS, it outputs to an mkv. People who use OBS may know that outputting to this format prevents a recorded video from being lost entirely if it crashes. The problem is that websites like Twitter only uploads for mp4 files in the h.264 codec. I've resolved this before by opening up Reaper or Shutte Encoder that can use ffmpeg to render a new file in the correct format, but it's such a clunky process for a task that could be more efficient. 

### Installing FFmpeg

FFmpeg is a free program used to convert videos from one format to another. As mentioned previously, Reaper and Shutter Encoder both use it to work with video. Many open source programs that work with video use it as well. Installing it on windows recently go really easy if you have WinGet. WinGet is a free package manager for Windows that could be its own separate topic. I use it all the time to update software and install new software with little to no hassle. It's called App Installer in the Microsoft Store. Once you have that installed, you can open up Command Prompt or Powershell and run:

<code>
winget install Gyan.FFmpeg
</code>