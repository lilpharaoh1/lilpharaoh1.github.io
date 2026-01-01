---
layout: post
title: A Missing Piece in Assistive Robotics
date: 2026-01-01
description: A long-ish read on a concept from neuropsychology and HRI  
# tags: formatting links
# categories: sample-posts
---

A few months ago, I started my PhD at the newly founded Centre for AI in Assistive Autonomy at the University of Edinburgh. Recently, we held our “Centre Day” where we shared the mission of the lab with the wider community: “How can we go from human-level intelligence to human-level collaboration with robots?”. In that mission lies my own work.

Rather broadly, I am looking at developing shared autonomy with robots. Essentially, how do we build robotic systems that allow humans to augment or extend their ability? Of particular interest to me is how we do this while maintaining the human sense of being in control and in the “decision-making chair.” Trying to answer these questions, roboticists alike often neglect to consider directly a critical element of these technologies. That element is the user’s sense of agency.

In this blog, I’m going to briefly outline what sense of agency actually is, why we should even care about it, and what roboticists like myself should do going forward with this information in mind. This blog is not a literature review. It’s not a perspective paper. It is primarily aimed at people who are interested in robots and human-centred AI, irrespective of background or prior knowledge. I also hope it’s not too bad for you folks that aren’t interested in either.

***

### What is SoA? Psychology and Neuroscience

Sense of agency (SoA) can more formally be defined as a person’s belief that their actions have a perceptible effect on the environment around them, along with the feeling that they are the originator of those actions.

Let’s illustrate this with an example. Imagine trying to use a pair of scissors to cut a piece of paper. Assuming you are capable of doing so, you might feel a sort of ownership over the use and outcomes of the tool, the scissors in this example. You think about doing the cutting, you do it, you see the result. The scissors may have done the cutting, but ultimately you feel that *you* completed the task. This is SoA at work.

There are three core components that contribute to this feeling; the ability to plan executable actions, initiate these actions, and perceive their effects.

Let’s consider another example to illustrate this. Forget the scissors and this time imagine a robotic hand that mimics the actions of your own hand clicking its fingers. If one of these three core elements of SoA is missing (you struggle to think of how you might use the hand to do the clicking motion, the actions the hand performs are delayed or disjointed from your own, or the results are perceptually different from what you imagined), you can expect your sense of agency and ownership over the robotic hand to be diminished.

A well researched theory of SoA in the human brain is the use of a comparator model. This fundamental framing of SoA suggests that humans predict how their actions will change their surroundings, and any error between their prediction and what they see manifests as a diminished or absent SoA. This model originates somewhat in cognitive control theory, in which the brain uses forward models to predict the sensory consequences of actions. This framing is not without its skeptics, however, as it doesn’t necessarily address the self-attribution aspect of SoA that we mentioned earlier (the idea that “I am the origin of this action and its consequences” rather than just “I did something that caused this result”). Yet, the comparator model is still often used to help us understand SoA in experiments.

Okay, so a definition and a theory are all well and good. But how did we come to validate and understand these concepts? How do we notice it in the brain? And how do we actually measure what seems to be something so fundamental to our understanding of our interaction with the world around us?

The first and most straightforward way of doing this is simply to ask participants what they experienced during an experiment. This is referred to as explicit measurement. After completing some task (playing a game, talking to a robot, whatever), participants are provided with an understanding of SoA similar to what I provided you with above. They then report their SoA using some form of scale or questionnaire. This method is generally biased and not super consistent; for example my four out of ten might be your seven out of ten. However, it is rather ubiquitously used in large part due to how practical it is to measure. Do something, report on how you felt. 

The other branch of measurements, implicit measurements, aim to quantify SoA with more objective and quantifiable methods. The most fundamental means of doing this relies on an interesting phenomenon known as intention binding.

Curiously, it has been shown that when participants perform an action that results in a stimulus—think pressing a button that triggers a tone, using a controller that moves a robot, or playing a chord that your bandmate should respond to—participants experiencing a SoA will recall the time between their action and the stimulus as being closer together than those who aren’t experiencing SoA.

Therefore, participants may be asked to complete some task in which this action–stimulus relationship is established. Once performing the action, they are asked for their estimate of the time between the two events. Shorter times, SoA. Longer times, no SoA. 

Other means of implicit measurements use physiological markers to determine SoA, with the primary approach being the use of brain scans to measure one’s attention response to their actions. Rather simplified, participants wear some neural monitoring gear (EEG) and the activation in a certain part of their brain is measured. If one believes their actions do not have an impact on their environment, i.e. they are not experiencing a SoA, this will be detectable in their brain activity.

From a research perspective, implicit measurements may often be preferable to explicit measurement as they provide researchers with some form of quantitative data that is less susceptible to reporting bias. However, this doesn’t imply that implicit measurements are completely objective and easily comparable. Implicit measurements can vary significantly between participants and even within the same participant over time, depending on task conditions and cognitive state. Additionally, framing an experiment in such a way that making these implicit measurements is possible is also not always the easiest task, and in fact may be prohibitively impractical in some cases. So choose your methods wisely.


### Why is SoA relevant in assistive robotics and shared autonomy?

To answer this question, let's think about what the world may look like if we do not consider SoA when building these technologies.

It has been demonstrated that more automation in assistive robotics leads to a greater loss of SoA and the feeling of control in its users. There have been multiple studies demonstrating that users often prefer reduced or no automation over greater levels of automation in assistive technologies, regardless of whether more automation leads to better task performance. It has further been shown that this observation is even more prevalent in environments that are more safety-critical or perceived as more personal or privacy sensitive.

The implications of this observation are rather profound if these technologies are to be widely adopted and not misused. How can we expect drivers to hand their lives over to autonomous vehicles or patients to trust surgeons with assistive tools if these technologies can’t even provide their users with the sense that they have control over the outcomes of their actions? Yes, this is rather dramatic, but it is a real consideration that can not be neglected.

This isn’t just a problem for safety-critical settings like driving or surgery. Shared autonomy, and therefore SoA, is a serious component for domains such as teleoperation, human-robot collaboration, or the use of prostheses and robotic arms by physically impaired individuals. In particular, users with some impairment may feel especially vulnerable despite their needs for such assistance, making maintaining a SoA an even more salient consideration. How do we make these technologies serve their users?

Despite people’s hesitation and aversion to the use of robotic assistance, especially when handing control over to robots, it has been proposed that there exists an individual optimal level and nature of automation that users desire in these systems. Hope may not be lost. Indeed, recent works on assistive robots that consider user’s SoA are popping up with increasing frequency. So what conclusions can we draw? How do we build assistive technologies that feel natural, fluid, and satisfying to work with?

### What contributes to SoA and how do we do better?

There certainly is a lot in this question and a tremendous amount of work that has tried to answer it. This blog post, and my own understanding, will by no means be able to comprehensively cover everything that is important. However, I can share what I have found, hopefully with the aim of jumpstarting your own exploration, or at least consideration of SoA. I’ll begin by looking at a fairly narrow means of improving SoA in a shared autonomy system, and then explain why I do so after the fact.

One clear trend across neuro-psychology and human-robot interaction is that the magnitude of robotic interventions in shared autonomy appears to matter much more than the frequency of intervention. What do I mean by this? Consider a robot helping you swing a golf club. Rather than adjusting your motion once you’ve gone off track, interventions should be frequent but minor, minimising the difference between your intentions and the “right” actions at each time step.

This implies that the future of assistive technologies must be capable of predicting both your intentions, the future results of your actions, and the consequence these actions have on the state of the task – “Will this result in a hole-in-one?”, “Is this drone landing position stable?”, “Will this vehicle trajectory result in a collision?”. Furthermore, they must be capable of adjusting this process such that we get the outcomes we want.

There have been methods proposed that do this primarily with the approach of first estimating both the human’s intentions and the degree of deviation from the optimal way of performing the task, then minimally adjusting the human's actions to be closer to that optimal trajectory.

The estimation part is critical and may be done either with machine learning of many kinds or with something closer to rule-based algorithms. The prior gives the benefit of machine learning’s ability to develop rich understandings from data, however at the cost of explainable guarantees of its behaviour. The opposite is true for the rule-based algorithms.

Generating interventions is slightly more straightforward but by no means a trivial task. This is typically done by blending the actions of the human and the robot to different degrees depending on the level of automation necessary to maintain safety/performance/whatever. The key element relevant to SoA is taking the disagreement between the predicted human actions and the actions that are executed by the robot as something to be minimised at every time step. Doing so intelligently, such that larger interventions are not necessary later in the task, requires an understanding of the effects of interventions through time and planning effective interventions with this in mind. This can again be done with machine learning or other methods, with the same tradeoff I mentioned a moment ago to be considered.

If we take a step back, how/where might these methods be used? Well, if our task is goal-directed, clearly optimizable, has a relatively low decision space, and a relatively low diversity in reasonable “ways to achieve the goal”, then these methods are sufficiently applicable. This comment isn’t made to be disparaging, in fact this strict formulation covers a lot of robotics tasks. Think robotic arms bringing food to a person's mouth, prosthetic legs augmenting a person’s gait, teleoperated arms reaching for an object, etc. Shared autonomy and SoA have primarily been explored through tasks such as these, and most research looks at similar applications.

However, how do we maintain SoA in a wider range of tasks? What about shared autonomy in tasks with multiple or ambiguous goals? What if goals are conflicting and high-level disagreements arise between human and robot? Further, how do we maintain SoA when these conflicts arise?

Let me explain this with an example. Think of a vehicle with assistive autonomous driving approaching an unsignalled junction. The junction is busy with vehicles coming from all directions making it difficult for the driver to assess. Once the junction appears to clear up a little and they’ve decided “let’s go now!”, the driver begins to step on the accelerator and adjust the steering wheel. What exactly should an intelligent assistive vehicle do in this situation? Imagine the maneuver is unsafe – vehicles are still approaching a little fast, or a pedestrian is considering crossing the road. Should the vehicle stop them? Or should it try to complete the maneuver as safely as possible, potentially violating social or road rules? Do we value that we maintain the drivers control and SoA? Or should we prioritise some beliefs embedded in the automation system as to what’s safe or acceptable in such a scenario?

These questions are being and have been explored in the work of many HRI researchers, however I am unaware of a definitive solution to these intersecting problems. In my opinion, the direction of shared autonomy research and the role of SoA has zoomed in on either low-level joint control conflicts (“how should we move the robot to augment the human to complete a task”) or high-level joint decision making conflicts (“how can the robot and human come to decisions together to complete a task”). However, these approaches have not been unified in domains in which both are present, such as our assistive driving example. Especially from a shared autonomy perspective. An interesting question I think, and one to really consider for future research. 

A mere blending of robot and human actions will not suffice in these domains. But if not that, then what? Potential answers may involve shared mental models, nuances in communicating explainable autonomy decisions, or maybe leveraging knowledge from neuroscience regarding prediction processing and cognitive control. How these insights may be applied to real-world robots is still, for the most part, unanswered.


