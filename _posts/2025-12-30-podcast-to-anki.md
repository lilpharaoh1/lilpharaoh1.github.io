---
layout: post
title: Podcast to Anki
date: 2025-12-30
description: Tool chain for converting podcasts to Anki flashcards
# tags: formatting links
# categories: sample-posts
---

Here’s a little tool chain I gathered together for turning podcasts on Spotify into Anki flashcards. I’ve found it useful for solidifying my knowledge on some history topics I find important enough to warrant a bit of extra work. The same tool chain might be adpated and used for YouTube videos, lecture notes, and things like that.

***

### Podcast to Audio
Export the podcast share link from Spotify and paste it into [this website](https://podcastmp3.com/). 

### Audio to Transcript
[This tool](https://evernote.com/ai-transcribe?utm_source=bing_ads&t_s=bing&t_cid=486538556&t_agid=1236951695996363&t_crid=kwd-77309867476291:loc-92&t_crname=text%20transcribe&t_match_type=p&t_network=o&t_device=c&t_gcid=&t_validation=486538556&msclkid=4385ff14a86e1f8fdd5d978915fb292d) from Evernote gets the transcript of the audio clip. I think there’s a limit of an hour, so if the podcast is too long split it up using whatever free audio editor comes with your machine. Save the output to a text file (you can use Notepad or [this tool](https://texteditor.co/) if you need).

### Transcript to Q&As
Once you have the trancript, input it into ChatGPT using the following prompt with the transcript text file attached. You’ll get a bunch of Q&As in the form: “What is the question? | Here is the answer.” Save the output into a text file.

> You are a world-class Anki flashcard creator that helps students create flashcards that help them remember facts, concepts, and ideas from videos. You will be given a podcast transcript. 
>
> 1. Identify key high-level concepts and ideas presented, including relevant equations. Ignore ads in the podcast transcript. Focus on facts. 
> 2. Then use your own knowledge of the concept, ideas, or facts to flesh out any additional details (eg, relevant facts, dates, and equations) to ensure the flashcards are self-contained. 
> 3. Make question-answer cards based on the transcript. 
> 4. Keep the questions and answers roughly in the same order as they appear in the transcript itself. 
> 5. If there's a source for the fact provided, please include a brief reference to the source. 
>
>Output Format, - Do not have the first row being "Question" and "Answer". - The file will be imported into Anki. You should include each flashcard on a new line and use the pipe separator | to separate the question and answer. You should return a .txt file for me to download. - Put everything in a code block. The podcast transcript is attached to this prompt

### Q&As to Anki
Import the Q&A text file into Anki by clicking the *Import File* button and selecting the text file you have just created. Make sure the field seperator is set to "pipe" and that the first few question look alright. Select the deck you'd like to import the cards to (so you may need to make one before importing) and you should be good!

*** 

This tool chain was largely inspired by [this prompt](https://ramjad.notion.site/10x-Anki-Prompts-1e522ee862c880a68d8bd19c0dca015d) that makes Anki-compatible Q&As from YouTube videos. Hope you enjoy!


