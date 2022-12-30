---
title:  "My first year as a public speaker"
---

It's the end of December, a great time for doing a retrospective of my first year as a public speaker.

I wanted to speak at a conference for a long time. I had already done "Brown Bag Lunch" (BBL) presentations inside Sonar, demystifying technical topics to a mixed technical and non-technical audience (for example, Object Oriented Thinking). My talks have been appreciated and this feedback encouraged me to think about widening the audience.

# DotNetDay Switzerland 2022

[.NET Day Switzerland](https://dotnetday.ch/) was the first time I spoke on a stage. It was awesome. However, I had prepared very well for it.

## Choosing a topic

After I read Alex Bîrsan's [Dependency Confusion: How I Hacked Into Apple, Microsoft, and Dozens of Other Companies](https://medium.com/@alex.birsan/dependency-confusion-4a5d60fec610) article in 2021, I did a one-week investigation sprint at Sonar to make sure we were safe. Afterwards, I did a small technical presentation to the Languages Team, explaining the attack. Alex, one of our Product Managers, suggested then to do a BBL for the company. In the following months I gathered some ideas on how I could present this to a non-technical audience, but did not invest the time in making the presentation.

## The opportunity

At the end of March 2022, I found out that the Call for Speakers of .NET Day Switzerland 2022 was still open and I could apply. Our VP of Products asked me whether the .NET Bubble wants to present something. I asked my team mates, no one really wanted to, so I wrote down three ideas. One was about "Dependency Confusion" (I already had a sketch for the talk), the second about "Improving the performance for Roslyn analyzers" (we had invested some time in this topic in the previous 18 months for our .NET analyzers) and another one about how "Symbolic Execution" works (a geeky topic, and we had in-house Control Flow Graph and Symbolic Execution Engine implementations).

Unfortunately, I didn't have time to prepare the titles and the abstracts, so I sent an email to the organizers for a deadline extension, and Manuel Meyer replied that I could apply until April the 10th.

I applied with the "dependency confusion" and "improving the performance" talks, and the first one got accepted on April the 12th. 

## Preparing

I knew from my previous BBL experience that preparing a good talk is not easy. And this time it wasn't a 15 or 20 minutes talk as before, but a 50-minute one.

I didn't have a lot of time - it was already mid-April and I had to have it ready by the end of August, and I had nothing yet, except two sheets of paper with a sketch. I had to have a plan. So I set myself some intermediate checkpoints:
- do a BBL explaining how the attack works to a non-technical audience by the end of May
- present the talk at two user groups before going on the big stage - forcing myself to have almost-ready versions that I could get feedback from .NET developers. Initially, I wanted to do one by the end of June and one in August.

## The BBL

I planned the BBL inside the company on the 2nd of June. It was good because I prepared the slides to explain in a visual manner was a package manager does and how the dependency confusion attack works. At this point, I created the Mr. Evil Hacker persona, which was very appreciated by my colleagues. I was watched by roughly 200 persons, some of which gave feedback on the hallways and via Slack, giving kudos for how well I helped non-technical people understand the concepts. Also, some of my technical colleagues gave kudos for raising awareness and with one we've discussed on how defending against it might work in the Java world.

## .NET Iasi virtual talk

I wanted to give a virtual talk at the [DotNet Iasi meetup](https://www.meetup.com/dotnetiasi/), and an in-person one at the [Geneva .NET User Group](https://genevadnug.ch/). Unfortunately, the Geneva organisers asked me the slides before, and I didn't have them (I was using the meetups to motivate myself to reach intermediate checkpoints), so I only got a slot on August the 10th for DotNet Iasi. In hindsight, this was a good thing, because I would not have had the time to prepare something for the end of June or beginning of July (my suggestion for the Geneva DNUG).

For DotNet Iasi, I had to prepare quite a lot, and it took a couple of weekends to do it: change or improve the existing slides to fit a .NET technical audience, add new slides to explain how to defend against the attack and create demos for the attack, as well for the defense. Moreover, I also added Typosquatting to the presentation (which meant: more demos, more slides).

The talk was fine, although I hadn’t had time to prepare my speech properly. It took a little bit more than one hour - I preferred to have more material that I could remove from for the 50-minute presentation. I didn’t get many questions as I wished at the end. Unfortunately, no tricky question. Even if I prepared a feedback form, I only got one feedback from it.

## Dry-runs in my company

The week before D-Day (the 30th of August 2022), I did three dry runs inside the company. The first one was during the .NET Guild Coffee Break (a cross-team meeting for the .NET developers in Sonar), on a Tuesday, hybrid. Then on Thursday I did one in-person only with around six people, and on Friday I did another one remote-only with four colleagues. I got plenty of useful feedback on the format of the presentation (slides, speech, story). Not that much on the content itself. And my colleague Andrea pointed me to Patrick Winston’s “How to Speak” MIT lecture, which I watched over the weekend.

## The weekend before

The weekend before I initially wanted to chill. However, I went to the local library and I borrowed some books about public speaking. While I was waiting on Saturday evening at a barber’s shop, I was polishing my slides on the phone (greatly simplifying them and making them prettier) according to Prof. Winston’s advice. I considered some hints from the books I skimmed through, although I must admit the “How to Speak” lecture was far superior to what I found at the local library. Even more, the books told me what (not) to eat and drink before the day, and I became stressed by this, too.

On Sunday evening I was still changing the demos a bit. The presentation was due on Tuesday morning.

## The D-Day

Initially, I though I wouldn’t be nervous, why would I? I had previously spoken in front of large audiences at my company. However, I got an upset stomach the day before the talk, probably due to stress. Thank God, the problem of eating got solved - for breakfast, I only ate toast with a little bit of feta cheese, and drank some tea.

In the morning, I joined my colleagues at the Sonar booth (after my talk got accepted, Sonar decided to sponsor the conference). Then I went to the opening key note (a brilliant talk by Mr. Richard Campbell on the History of .NET - very well delivered, I must say). I stayed at the Sonar booth for an hour after, to calm my thoughts and allow my colleagues to go and watch some talks in the first batch. There wasn't much activity at the booth, so I could calm down.

Fortunately, my talk was scheduled at 10h45, in the second batch, so I did not have to wait a lot. I went there 15 minutes before the talk, as instructed by the organizers. I met the volunteers from the local Swiss .NET community. I plugged in the laptop, verified the contrast of the console and the IDE, changed it from dark to bright at their advice. Attached the microphone, prepared the “Evil Hacker” outfit for later in the talk when I would need it, and I was ready.

I did not have any stage fright. On the contrary, I felt like a fish in the water. My colleague Mary told me there were 50-60 people in the cinema room, less that a normal “Sonar” BBL audience. I had great fun, I did not have any irreparable demo effects, the audience laughed at the “funny” moments. I managed to deliver the talk on time, finishing a couple of minutes earlier. 

Furthermore, I got great feedback from people later during the conference. The “Evil Hacker” persona was very well received. And I also got nine pieces of feedback via the feedback form I put on my website. Most of it positive.

Thank God, I accomplished my mission.

There were other cool stuff like the speakers dinner (I got to talk with Richard Campbell for two hours on a variety of topics) and having breakfast at the hotel the second day with renowned speakers. Maybe I’ll write about that at a later date.

# VisugXL Belgium 2022

In September I had applied to another .NET community conference at the end of October, this time in Belgium, and got accepted. I changed the title from “” to “”, because one of the feedback I got was that the title was very confusing and mysterious. I also changed the description on Sessionize and included verbatim excerpts from the .NET Day Switzerland feedbacks in the "note to the organizers" section, to "sell" myself.

Before leaving to Belgium I did another dry run - two months had passed since my talk in Zurich, I had to rehearse my talk and the demos. This time, I did it alone, as I was confident on the quality of my presentation. Also, I had modified the slides a little, improving them and adding more content, as this time I had a 60 minutes slot. I removed some slides from the beginning which I considered not so important and I added a “use a lock file” section in the presentation.

Because Sonar paid for the plane and hotel, the organizers gave us a sponsor table at the conference (VisugXL is a small one-day conference, on a tight budget). I went there alone, as a one-man team - I stayed at the booth from morning ‘till I entered the conference room at 15h45. It was a great opportunity to talk with various people, both who knew our products and had various questions or remarks, as well as people who never heard of SonarQube or SonarLint before.

This time I had 26 people in the room, as opposed to the experience in Zurich, here the audience was much more interactive - they were asking questions on the go, which was quite nice. And at the end, we spent roughly 15 minutes discussing various topics. I went over the timebox, but it was the last presentation so that was ok (I planned 50 minutes of presentation and 10 minutes of Q&A, but all in all there were around 20-25 minutes of Q&A instead, hence the spillover). That was a great learning experience, because some of the folks in the room were quite senior and knew many topics better than me! Exposing my own ignorance and learning is one of the reasons started to speak at conferences.

At the end of the day, one of the organizers who watched my talk told me that I could also apply for Techorama. For me, this small interaction was very rewarding.

# Geneva .NET User Group

The last session I gave was at my local .NET User Group in Geneva. It was on Thursday the 10th of December. Unfortunately, there were only five people in the room, but each of them appreciated the talk, said they learned new things they can apply in their day to day work, and this is a great reward for me as a speaker. The audience was again interactive, asking questions as I was speaking. From some of the interactions I got ideas of hobby projects I could do and I started to think about my next subjects.

# The rejections

This year was my first year as a public speaker. If you aspire to become a speaker at developer conferences, bear in mind I had applied to N conferences this year and only got accepted at two. I don’t know why, as they didn’t give me any sort of feedback.

I don’t plan to stop here, I have some ideas for other talks and I will try to get accepted at bigger developer conferences.

2023, here I come :)
