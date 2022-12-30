---
title:  "2022: my first year as a public speaker"
---

> The mind cannot continue in one and the same condition, I mean without receiving addition to or diminution of its good qualities. For to fail to gain new ones, is to lose them, because when the desire of making progress ceases, there the danger of going back is present. (Abbot Theodore in “The Conferences of Desert Fathers” by St. John Cassian)

It's the end of December, a great time for doing a retrospective of my first year as a public speaker.

I wanted to speak at a conference for a long time. I had already done "Brown Bag Lunch" (BBL) presentations inside Sonar, demystifying technical topics to a mixed technical and non-technical audience (for example, on Object Oriented Thinking). My talks had been appreciated and this feedback encouraged me to think about widening the audience and speaking at a developer conference.

# DotNetDay Switzerland 2022

[.NET Day Switzerland](https://dotnetday.ch/) was the first time I spoke on a stage. It was awesome and, thank God, I nailed it. In this blog post I will explain how I prepared for it.

## Choosing a topic

After I read Alex Bîrsan's [Dependency Confusion: How I Hacked Into Apple, Microsoft, and Dozens of Other Companies](https://medium.com/@alex.birsan/dependency-confusion-4a5d60fec610) article in early 2021, I did a one-week investigation sprint at Sonar to make sure we were safe. Afterwards, around June 2021, I did a small technical presentation to the Languages Team, explaining how the attack works and what were the possible defense mechanisms at that time. Alex, one of our Product Managers, suggested that I do a BBL for the entire company. In the following months I gathered some ideas on how I could present this to a non-technical audience, but did not invest a lot of time in making the presentation.

## The opportunity

At the end of March 2022, I found out that the Call for Speakers of .NET Day Switzerland 2022 was still open. Our VP of Products asked me whether the .NET Bubble wants to present something. I asked my team mates, it did not spark a lot of interest, so I wrote down three ideas that came to my mind. One was about "Dependency Confusion" (I already had a sketch for the talk), the second about "Improving the performance for Roslyn analyzers" (we had invested some time in this topic in the previous 18 months for our .NET analyzers) and another one about how "Symbolic Execution" works (a geeky topic, and we had an in-house Control Flow Graph and Symbolic Execution Engine implementation).

Unfortunately, I didn't have time to prepare the titles and the abstracts, so I sent an email to the organizers for a deadline extension, and Manuel Meyer replied that I could apply until April the 10th.

I applied with the "dependency confusion" and "improving the performance" talks, and the first one got accepted on April the 12th. 

## Preparing

I knew from my previous BBL experience that preparing a good talk is not easy. And this time it wasn't a 15 or 20 minutes talk as before, but a 50-minute one.

I didn't have a lot of time - it was already mid-April and I had to have it ready by the end of August, and I had nothing yet, except two sheets of paper with a sketch. I needed a plan. So I set myself some intermediate checkpoints:
- do a BBL explaining how the attack works to a non-technical audience by the end of May
- prepare the presentation and demo for a technical audience
- present the talk at two user groups before going on the big stage - forcing myself to have an almost-ready version that I could get feedback on from .NET developers who could expose my ignorance on the topic. Initially, I wanted to do one session by the end of June and one in August.

## The BBL

I planned the BBL inside the company on the 2nd of June. It was good because I prepared the slides to explain in a visual manner what a package manager does and how the dependency confusion attack works. For this BBL, I created the Mr. Evil Hacker persona to explain the attacks.

I gave the talk from my desk, with almost 200 persons online, some of which gave feedback on the hallways and via Slack, giving kudos for how well I helped non-technical people understand the concepts. Some of my technical colleagues gave kudos for raising awareness. Everyone loved "Mr. Evil Hacker", they even screenshot me and created a slack :hacker: emoji out of it.

## .NET Iasi virtual talk

I wanted to give a virtual talk at the [DotNet Iasi meetup](https://www.meetup.com/dotnetiasi/), and an in-person one at the [Geneva .NET User Group](https://genevadnug.ch/). Unfortunately, the Geneva organisers asked me for the slides before, and I didn't have them (I was using the meetups to motivate myself to reach intermediate checkpoints). 

I got a slot on August the 10th for DotNet Iasi. I had to prepare quite a lot, and it took a couple of weekends to do it: change or improve the existing slides to fit a .NET technical audience, add new slides to explain how to defend against the attack and create demos for the attack, as well for the defense. Moreover, I also added Typosquatting to the presentation (which meant: more demos, more slides).

The talk was fine, although I hadn’t had time to prepare my speech properly. It took a little bit more than one hour - I preferred to have more material that I could remove from for the 50-minute presentation. I didn’t get many questions as I wished at the end. Unfortunately, there was no tricky question and no constructive feedback.

You can watch the [recording on youtube](https://youtu.be/ghKAGy-NrSI) - it was an ok talk, but my slides and speech were not polished and in my opinion I did not have a very good energy and vibe throughout the talk. I really needed to change this before going on stage.

## Dry-runs in my company

The week before D-Day (the 30th of August 2022), I did three dry runs inside the company - the full show, the "final" slides, the demos, the Evil Hacker change of persona in the middle of the talk. By this time, I improved the presentation, reduced the content and prepared a speech. 

The first dry-run was during the .NET Guild Coffee Break (a cross-team meeting for the .NET developers in Sonar), on a Tuesday, hybrid. Most of the feedback I got was related to the content (as expected, because they were the NuGet and MSBuild subject matter experts in the company). 

Then on Thursday I did an in-person dry-run with around six people and on Friday I did another one remote-only with four colleagues from various teams. I got plenty of useful feedback on the format of the presentation (slides, speech, story). Not that much on the content itself. And my colleague Andrea pointed me to [Patrick Winston’s “How to Speak”](https://youtu.be/Unzc731iCUY) MIT lecture, which I watched over the weekend.

## The weekend before

The weekend before I initially wanted to chill. However, I went to the local library and I borrowed some books about public speaking. While I was waiting on Saturday evening at a barber’s shop, I was polishing my slides on the phone (greatly simplifying them and making them prettier) according to Prof. Winston’s advice. I considered some hints from the books I skimmed through, although I must admit the “How to Speak” lecture was far superior to what I found at the local library. Even more, the books told me what (not) to eat and drink before the day, and I became stressed by this, too.

On Sunday evening I was still changing the demos a bit. The presentation was due on Tuesday morning.

## The D-Day

Initially, I thought I wouldn’t be nervous, why would I? I had previously spoken in front of large audiences at my company. However, I got an upset stomach the day before the talk, probably due to stress. Thank God, the problem of eating got solved - for breakfast, I only ate toast with a little bit of feta cheese, and drank some tea.

In the morning, I joined my colleagues at the Sonar booth (after my talk got accepted, Sonar decided to sponsor the conference). Then I went to the opening key note (a brilliant talk by Mr. Richard Campbell on the History of .NET - very well delivered, I must say). I stayed at the Sonar booth for an hour after, to calm my thoughts and allow my colleagues to go and watch some talks in the first batch. There wasn't much activity at the booth, so I could calm down.

Fortunately, my talk was scheduled at 10h45, in the second batch, so I did not have to wait a lot. I went there 15 minutes before the talk, as instructed by the organizers. I met the volunteers from the local Swiss .NET community. I plugged in the laptop, verified the contrast of the console and the IDE, changed it from dark to bright at their advice. Attached the microphone, prepared the “Evil Hacker” outfit for later in the talk when I would need it, and I was ready.

I did not have any stage fright. On the contrary, I felt like a fish in the water. My colleague Mary told me there were 50-60 people in the cinema room, less that a normal “Sonar” BBL audience. I had great fun, I did not have any irreparable demo effects, the audience laughed at the “funny” moments. I managed to deliver the talk on time, finishing a couple of minutes earlier. 

Furthermore, I got great feedback from people later during the conference. The “Evil Hacker” persona was very well received. And I also got nine pieces of feedback via the feedback form I put on my website. Most of it positive. 

Thank God, I accomplished my mission. The session was not recorded, but the slides I used are public on [speakerdeck](https://speakerdeck.com/dotnetday/dot-net-day-22-dependency-confusion-and-its-cure-a-nuget-story-by-andrei-epure).

There were other cool stuff like the speakers dinner (I got to talk with Richard Campbell for two hours on a variety of topics) and having breakfast at the hotel the second day with renowned speakers. Maybe I’ll write about that at a later date.

# VisugXL Belgium 2022

In September I had applied to another .NET community conference at the end of October, this time in Belgium, and got accepted. I changed the title from “Dependency confusion and its cure. A NuGet story.” to “How to attack a .NET software supply chain”, because one of the feedback I got was that the title was very confusing and mysterious. I also changed the description on Sessionize and included verbatim excerpts from the .NET Day Switzerland feedbacks in the "note to the organizers" section, to "sell" myself.

Before leaving to Belgium I did another dry run - two months had passed since my talk in Zurich, I had to rehearse my talk and the demos. This time, I did it alone, as I was confident on the quality of my presentation. Also, I had modified the slides a little, improving them and adding more content, as this time I had a 60 minutes slot. I removed some slides from the beginning which I considered not so important and I added a “use a lock file” section in the presentation.

Because Sonar paid for the plane and hotel, the organizers gave us a sponsor table at the conference (VisugXL is a small one-day conference, on a tight budget). I went there alone, as a one-man team - I stayed at the booth from morning ‘till I entered the conference room at 15h45. It was a great opportunity to talk with various people, both who knew our products and had various questions or remarks, as well as people who never heard of SonarQube or SonarLint before.

This time I had 26 people in the room, as opposed to the experience in Zurich, here the audience was much more interactive - they were asking questions on the go, which was quite nice. And at the end, we spent roughly 15 minutes discussing various topics. I went over the timebox, but it was the last presentation so that was ok (I planned 50 minutes of presentation and 10 minutes of Q&A, but all in all there were around 20-25 minutes of Q&A instead, hence the spillover). That was a great learning experience, because some of the folks in the room were quite senior and knew many topics better than me! Exposing my own ignorance and learning is one of the reasons started to speak at conferences.

At the end of the day, one of the organizers who watched my talk told me that I could also apply for Techorama. For me, this small interaction was very rewarding.

# Geneva .NET User Group

The last session I gave was at my local .NET User Group in Geneva. Like before, I did a dry run before, to make sure the demos still work and that I have a nice flow of ideas. It was on Thursday the 10th of December. Unfortunately, there were only five people in the room, but each of them appreciated the talk, said they learned new things they can apply in their day to day work, and this is a great reward for me as a speaker. The audience was again interactive, asking questions as I was speaking. From some of the interactions I got ideas of hobby projects I could do and I started to think about my next public speaking subjects.

# The rejections

This year was my first year as a public speaker. If you aspire to become a speaker at developer conferences, bear in mind that I applied to six conferences in 2022 and only got accepted at two of them. I have a better acceptance ratio at user groups (two out of two).

# 2023

2022 was a great year, I worked a lot for my public speaking debut, I learned a lot from the process, I met a lot of interesting people, I got a plethora of positive feedback and good vibes from the two conferences I participated at. 

Last, but not least, one of the .NET Day volunteers told me after my session: "I understood that this was the first time you spoke on a stage. You did very well, you really should continue doing this."

I don’t plan to stop here, I have some ideas for other talks and I will try to get accepted at bigger developer conferences next year. 

However, it will be a lot of work to get there, as I am doing this mostly in my spare time. 
