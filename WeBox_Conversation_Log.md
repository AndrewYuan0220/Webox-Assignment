# WeBox AI Quality Cockpit — Conversation Log

**Author:** Andrew Yuan
**AI collaborator:** Claude (Anthropic)
**When:** October 27–28, 2026, across two evenings
**What came out of it:** the Web PRD, the WeBox Kitchen prototype, the WeBox HQ prototype, this log, and talking scripts for Part 4

My messages are verbatim. I dictate by voice, so the typos are left in. The AI's replies are condensed to what it did. File contents, code and exported documents are left out.

---

## SparkNotes: how I work with AI

**The loop.** I ask the AI for its read. I answer with how I actually think, out loud and with concrete examples. It drafts, I review hard, it revises, and we repeat until it's right. That came to 29 messages from me over two evenings.

1. **The AI goes first, then I reframe.** My first real ask was "tell me what you believe this assignment to be." Its outline followed the brief: AI grades the food, and the rankings drive terminations. I redirected it. A photo can't judge food, so the chef-facing experience comes first. *(#2–#3)*
2. **I think in examples, not abstractions.** Ratatouille made with red and yellow peppers because the market had no good green ones. iPhone vs. Xiaomi color science. A plastic display dish. A hair in the rice. A chef who says "it's fine" twice without fixing anything. Every example became a feature or a test scenario.
3. **Bullets before documents.** "Don't create a document yet just give me the bullet points." We agree on the idea before building anything. *(#3)*
4. **I take pushback, and I push back.** I accepted the AI's points on a dispute window, holding orders for safety issues, and giving chefs a reason to use the tool. I held my ground on hidden scoring: it measures honesty, not food, and any concern comes from a person, never the app. *(#4)*
5. **I set the numbers.** Customer reviews 40%, honesty 40%, photos 20%. Major −10 and Minor −2. A conversation at a total of 60 or below, or when one component drops below 10. Minor dings happen once per pattern and never stack. *(#9, #14, #25, #26)*
6. **Line-level review.** I left inline comments on the PRD: "keep it within 10 words," and "photo score is there but only 20%." *(#8–#14)*
7. **I pick tools on value.** I asked what v0 and Cursor are, whether they cost money, and whether my existing plans would do. I built in Claude and made the test photos in Gemini. *(#16–#22)*
8. **I test it myself and report exact bugs.** "I repeatedly tapped that and it did not ding honesty whatsoever … make sure that repeatedly tapping it does not stack." *(#25)*
9. **The spec follows the product.** After every build: "update your PRD to reflect all the changes." *(#25, #28, #29)*
10. **I change my mind when the build shows me something.** Seeing the HQ app made me rethink three things:
    - Mandatory honesty scoring felt harsh, so the app became an optional pilot with a photo pledge.
    - HQ split into two roles: a reviewer and an administrator.
    - The reviewer gets to see integrity notes, judged blind to the restaurant's score.

    *(#28–#29)*
11. **I keep final say on design.** WeBox white and red for kitchens, a dark theme for the office, a centered camera shutter, and a gear icon instead of a sun. *(#24, #26, #28)*

**What held from the first message to the last**
- An image never judges food quality. The tool is insurance, not surveillance.
- Never accuse, always question.
- Respect the chef, and keep a person reachable at every step.
- Judge the vendor's reliability (customer reviews, honesty), not the color of the broccoli.
- Food safety first: a possible hair or bug is held, checked by a person and resolved in minutes.

## Timeline at a glance

| Phase | Messages | What changed |
| :--- | :--- | :--- |
| Understand the brief | #1–#2 | AI's first read follows the brief as written |
| Reframe around the chef | #3–#6 | "Never accuse, always question," Today's Notes, honesty over food scores |
| Technical web PRD | #7–#14 | PRD rebuilt in a web template, with my concerns up front; inline edits; the 40/40/20 split |
| Choose the pipeline | #15–#22 | Build in Claude; test photos generated in Gemini |
| Kitchen prototype | #23–#25 | Chef app plus a live server view; safety hold, false alarm and honesty dings |
| HQ prototype | #26–#27 | Six restaurants covering every outcome, the thresholds, and a test plan |
| Rethink and finish | #28–#29 | Optional pilot, photo pledge, Reviewer and Admin roles, blind integrity review, final polish |

---

## The conversation
### Phase 1 — Understanding the assignment

#### #1
> Ok, Create a new project We are creating the test assignment for Webox.

**AI (condensed):** Looked for earlier WeBox context, explained that it couldn't create a claude.ai Project itself, and waited for the brief.

#### #2 · "Tell me what you believe this assignment to be"
> This is the assignment for the webox project I would like you to go through it and tell me what you believe this assignment to be and outline this project to your best understanding, I will let you know what I think about it after you are done

*(Assignment PDF attached.)*

**AI (condensed):** Looked up WeBox's business (San Jose workplace food platform working with restaurant partners). Explained the assignment as a take-home testing scoping, AI–human trust, data-driven decisions and AI-tool fluency. Listed gaps needing assumptions (where photos are taken, who the users are, what a photo can and can't detect). Outlined a submission: PRD with site map and AI logic flow, dispute workflow, 30-day trends, JSON schema, two prototype screens, prompt log and case study.

---

### Phase 2 — Reframing the product around the chef

#### #3 · Respect the artisan
> OK so I think you have a pretty good grasp on the whole thing. However I want to align your focus to something a little bit different, I want you to emphasize and the PRD about empowering the end users as it is intrinsically an extremely condescending method to have an AI judge the work of an artisan like a chef. I want you to first question this interview assignment as a whole because I believe this system is a source of many many issues and I believe fundamentally if implemented wrong or if overly reliant to something like this this is going to take a huge hit on the supplier side of the company as this tool can always and underline always only be used as a reference. A picture or a video shall never be used as the only judge of what a food is. I want to give you an example so that you can take some notes on for example if I am a chef and I am doing a Ratatouille, however in the market that day there were no good green bell pepper So I decided that I am going to replace the green bell pepper with yellow and red ones and that is something that the AI wouldn't know as a green bell pepper will look significantly different than a red and yellow one and it will trigger some alarms immediately with a visual only detection system. No matter how smart the AI is sometimes the human instincts on picking the right ingredient for their dish is immediate and incomprehensible with no matter how complicated a digital system can be. So what I want you to shift this focus to is creating not just a dashboard for the higher ups which of course that's important but I want you to first start with creating a interface that shows the utmost respect for the artisans that are creating the dishes. It may not be condescending, So what does that mean being condescending I believe a system where you take a picture and after some AI beep boops It gives you a score against a A hidden rubric that cannot be seen. This is disrespectful and could potentially harm The relationship between our platform and the chefs. So first of all before we go even anywhere into the actual system for the back end I want you to take all of what I am saying into consideration. The interface That the chefs or restaurant managers take on site I believe is a lot more important than the background analyzing software as the analyzation software There's really no Way to go wrong. However what I am thinking with the user facing software for the restaurant owners, It should first of all keep it very Clear on what this program does, what this program does is it analyzes the portion size, it analyzes the color of the ingredient, it analyzes anomalies such as bugs or human hair in the food, however what it does not do is grade the chefs who made the food, display the rubric first and establish the fact that this is a tool but not a All knowing God that judges your food. These chefs most likely have pride that they want to maintain and the last thing they want is for an AI to tell them what they are doing wrong, even worse an AI that they are being forced to use, not of their choice. That is the main thing I want to maintain. The second thing I want to in courage in the design of the main program is always put a floating bubble to directly contact a LOM agent that can directly answer any questions, and if the question become too difficult and it should directly be able to reach a member of the team for manual review, that option should never ever be covered or hidden away any menus as this direct communication is always the most important thing. And then last but not least once the image is taken of the food, Don't give a one and only grade for the food, what you need to give is a pass or a question mark. Let's say portion size, If the portion size was significantly smaller then the optimal image, it could totally not be that the portion size changed, what if they switched to a different box? So never say you fail always say Are you sure this is the same as what we are judging against? The interface of the chef should contain four drop down boxes or more if you see The need for more of them,, one for each criteria. First one is the portion, the second one is the color freshness, the 3rd is for Foreign objects like bugs, and the 4th Is for overall presentation Like plating and stuff. Each of the sub criteria have a short paragraph describing why the LLM decide to pass or raise concern this particular dish on that criteria. And when that concern is raised make sure there is a big button right underneath to say dispute, and also say retake the photo. So re take the photo is basically a button That says Yep, I did something wrong Let me fix that and let's try again. Dispute is so you can submit what you want to say about this situation, and first of all LMM will identify Whether the chef makes sense or the restaurant manager makes sense to question, yet the confidence score is low of course you do the thing where it connects to a human verification person. Make sure throughout the entire process that app has multiple avenues to directly connect to someone that is on the other side and can answer questions, AI or human alike. Never leave the restaurant manager or chef hanging with a question that they don't have an answer to or a problem with our program that they cannot raise. This is empowering the user. I think the rest of whatever you are saying is also really good and the logic flow everything is great but I just want you to remember this is what I want for this app and this is what I believe is right. Regarding the workflow I believe the rest of the workflow That you have highlighted has been correct so I want you to give me short rundown of the PRD using what I have said, don't create a document yet just give me the bullet points Don't create a document yet just give me the bullet points. What I want you to remember Is that all of the no scoring for these dishes are only for the client side which is the chef and the restaurant manager, the scoring is going to be kept secret and sent directly to our back end in which if there is no questions from the restaurant side nothing has been flagged as wrong or right No nothing has been given from them we log them then we lock them in

**AI (condensed):** Critiqued the assignment's premise (a photo shows only part of a dish; rankings for termination turn partners into suspects; rigid scoring invites gaming). Produced a bullet-point PRD: principles, onboarding showing what the tool does and doesn't do, a "Today's Notes" field for declaring substitutions, per-criterion Pass / Question sections, Retake and Dispute buttons, always-on help bubble, hidden backend scoring with log-and-lock. Pushed back on five points: the AI can be wrong, hidden scoring needs disclosure, lock-in needs a dispute window, foreign objects need a hold, and chefs need a reason to use the tool (proof the dish left right).

#### #4 · "Never accuse, always question"
> Very good I want you to add in the principles The AI is a reference tool not a judge, every flag is a question never a verdict no matter the confidence level of the AI. It doesn't matter if it had 100 percent confidence, if the vendor or the chef has something to say they can always override in AI's decision and trigger an internal review. That today's notes section is very good I want you to expand a little bit more upon it S and this will become a differentiating factor between my methodology of creating this assignment and I would say potential other interviewers this will set me apart. And the result as expandable sections per criteria I agree that looks really good, and I want you to focus on one keyword or one key phrase that I want to bring up is never accuse, always question. And then the question is raised, two large button directly underneath where the retake or re judge button. That will not visually change any of the grading above ground which is something that they will see but it changes the grading behind the scene if it is retaken and the image looks Substantially different, I think there is many easy way to trick the system. I want to question the system in the fundaments like if they're judging for color for freshness what if the chef just adds a filter to the picture they're taking? It might be able to be resolved through 0 you have to take the picture live within our app, But even the brand of Phones have different color science for their camera, just for example an iPhone usually have a duller and more realistic color science Which will look less vibrant than a lot of Chinese based Android phones such as the Xiaomi which sometimes automatically applies a filter to a picture. In essence what I want to point out is that there is no way a single picture or a single video can be the physical and all be score for a dish. There should not be grad granulated scoring for the actual dish based on a zero to one 100. The score should come from how much do you think the chef or the restaurant is trustworthy if they have to retake the picture 4 * 5 times to pass this it means they're probably a little bit sloppy behind the scenes and that should be The red flags that get raised instead of in objective scoring of the dish itself based on the color based on the scaling etc. This grading system for the restaurants should not be based on each image but it should be based on trust. If a restaurant repeatedly try to cheat the system by taking a photo of another photo of the dish or if they have created our gold standard dish as a plastic model, that should be immediate red flags instead of actual dishes that looked a little bit less colorful. And then when the chef clicks the dispute button yeah I believe what you are doing is correct confidence is high I think it will just record this interaction for further review that can be conducted every month for a restaurant either done by a human or an LLM of the amount of times that something has been flagged and how the chef explains himself. If the confidence is low yeah the dispute should go through a human reviewer and the one thing it needs to do is to give structural timelines like saying oh currently this image is being Assigned to a reviewer, and then there is a next step which is currently being reviewed, and then the review being sent there should be A 3 step process and the chef should not be left in the dark during any of those, he should give expected wait times and a clear step by step on what is happening step by step on what is happening. And the command center the supplier performance engine 30 day trends that is good but I believe the scoring criteria above So I think whatever scoring engine it needs to score on it needs to put a heavy emphasis on the trust of each of the restaurants and the amount of times they have to go through our system and the believability of their disputes instead of a zero to 100 score on each of the criteria as I previously have said. And yes I agree with the things that you will push back, the analysis software absolutely can go wrong I did not say it cannot go wrong and I just explained earlier why it can, And the hidden scoring I don't believe is disrespectful but As I previously explained I am not scoring them based on the food quality judged by just one image, we are basing the scoring based on the amount of time they have to interact with our system the amount of effort we have to put into human judging and the amount of times that it is actually a false positive versus a true positive where there's a problem that is the true scoring system that we are gonna be using. And it is right for the user to not see that. We should notify them that such a quality trend metric is being tracked but we should never tell them if we are currently having you know a problem with them directly from the app, If such a problem exists it should be a separate email that is sent because our app doesn't have the authority to tell them if what you have been doing is good or bad. Lock it in when nothing is raised I agree there should be a window and for an object can be soft I also agree so always just raise them as questions and from what I understand if you have a bug in the bish you should not just remove it and send it out I think when a foreign object or Potential food safety risk is detected with a high confidence it should automatically go to a human reviewer, It should be marked as urgent and it should be resolved immediately. And the give the chef a reason to use it frame each photo as proof of the dish let the let the chicken right no left the kitchen right Yes that's a very good point yes I believe you have to put that in the sales document for this program so that the chefs do use it. OK now I want you to create me rough draft of this PRD. This is a rough draft so don't go too crazy on the formatting. use .md format, And I want you to make sure you go into quite a bit of depth questioning the ability of one image judging a dish and the existence of such gold standard for any of the dishes I want you to question this interview assignment very harshly before starting talking about anything with actually resolving this problem. Also Reiterate what we are going to be using this system for, not for judging restaurants but for insurance. Because remember, an image does not tell you the quality of the food and anyone who says otherwise is wrong.

**AI (condensed):** Wrote the rough-draft PRD in Markdown. It opens with a hard critique (a photo is not a dish; the Gold Standard doesn't exist; phone color science; gaming; false precision; supply-side damage), then the insurance framing, principles ("never accuse, always question"), expanded Today's Notes (quick chips, structured substitutions, voice, multilingual, living standard), live in-app capture with a color reference card, retake chains judged behind the scenes, dispute flow with a 3-step tracker, urgent safety holds, a trust score instead of dish scores, integrity red flags, HQ Command Center, site map, AI logic flow, JSON schema, case study and success metrics.

#### #5 · My reasoning, dictated as notes for a separate talking-points doc
> Okay no I'm just going to ramble for a stuff that I will be talking about during the interview that I want you to take notes of. First I want you to establish the fact that there is a fundamental flaw with the premise of this application of judging the goodness of food using one picture and I want you to use the xiaomi versus iPhone camera and the Ratatouille example to back it up. And second I want to establish the fact that it is very disrespectful for especially the older chefs who may be run a family restaurant for years and they don't want to be pointed and judged by an AI. That is very potentially disrespectful and could cause friction between us and our suppliers. And third I believe there is really not a lot of different ways you can present data. But how you gather the data through what method is going to be the most important thing here to being respectful at all times. And I also believe it's not about how much data you collect and how much assumptions you make with such AI, but it's about what data you collect. Since we have established that using a photo to judge food is a flawed concept in the very beginning, I would like to not use the actual score that came out of the AI from the criterias to be the important data that we collect. What we shall collect is qualitative data from the chefs and customers and what they have to say about that dish The amount of times they have to raise a concern against our AI and the amount of times for the consistency of the dish. Sometimes a good dish is best when it's not consistent because a true good chef chooses the best ingredients and there is I believe no such gold standard, and even if there is it cannot be judged by a photo. So we use this tool instead of checking the quality of the dish we check the reliability of the vendor in how often it tries to lie cheat their way through our tests and combining that with customer reviews of the dishes we can give a good overall vendor score instead of using the pictures. This is my main focus for doing this assignment. I want you to turn this into a separate document for just random notes I want to drop down for the actual interview where I have to explain all of this

**AI (condensed):** Turned these into a separate notes document with five themes:
- the flawed premise, with the ratatouille and iPhone vs. Xiaomi examples
- respect for long-running family restaurants
- how the data is gathered matters most
- what data matters, not how much
- judging the vendor's reliability by combining honesty with customer reviews

#### #6 · What we actually judge
> I want to make sure that you include the following points: What we are trying to judge is not the goodness of the food using this program, but we are trying to judge the reliability of the vendor. What get waived a lot more during the final judgment for each of the vendors are not on the greenness of the broccoli, but on a mixture of positive customer reviews, and they're honesty. If a restaurant is caught trying to weasel their way out and cheat this program. Such as uploading an image of a fake food, an image of an image, that when it is identified by our AI actually gets a huge deduction to their credibility score. And when the chef or restaurant manager is willing to lie about their food and trick the AI into not raising a question about it anymore, if such behavior gets caught that is what we are grading each vendors on.

**AI (condensed):** Added these points:
- The final judgment rests on customer reviews and honesty, not the color of the broccoli.
- Fake food, photos of photos or screens, and lying to the AI cost a large deduction.
- A paler dish or an honest substitution costs nothing.

It kept one safeguard: a person confirms a caught cheating attempt before the deduction sticks.

---

### Phase 3 — Turning it into a technical web PRD

#### #7 · Rebuild in a web PRD format, with my concerns first
> Okay so this is what a PRD that is you know web-based and you know more technical is supposed to look like this is a answer from another AI and I would like you to access all the links to see all of the examples of a good web PRD and I want you to rebuild your PRD in this format however before you start I want you to insert in the very beginning my concerns and what I have decided to do instead of actually you know following everything to the tee

*(Web PRD template from another AI attached.)*

**AI (condensed):** Searched for the referenced examples (Unchained storefront PRD, PostHog's public handbook; one reference couldn't be found). Rebuilt the PRD in the web template format, opening with a new Section 0, "My Concerns, and What I Decided to Do Instead," plus a table mapping each brief requirement to how it's still delivered. Added routes and access gates, deep linking, responsive breakpoints, offline capture, Core Web Vitals targets, web camera integrity, accessibility and languages, 13 features with user stories and Gherkin acceptance criteria, Mermaid flow diagrams, a `chef_facing` / `internal` JSON schema, phased rollout with feature flags, and an analytics event list.

**Inline review comments on the web PRD.** Each one was left on a highlighted passage.

#### #8 · Comment 1
**Highlighted:** "…That is condescending, and it insults the people who make our product."
> I am thinking Does the chef make our product or are they counted more as our supplier

**AI (condensed):** Confirmed they are suppliers (independent restaurant partners), which strengthens the business-risk argument. Reworded to "the independent partners who cook the food our clients actually eat."

#### #9 · Comment 2
**Highlighted:** "operational" (in "customer sentiment + honesty + operational reliability")
> Not really operational reliability I think we are still going to rate the food on the colors and everything so the images are still going to rate the food however the split of score should be 40 on the customer reviews 40 on the honesty and 20 so a very small amount on the actual what the camera with the picture grades the food at

**AI (condensed):** Changed the vendor score to customer reviews 40%, honesty 40%, photo check results 20% throughout the PRD. Moved retake patterns and dispute believability into honesty. Counted only final photo results (after the dispute window or review), excluding overturned questions and declared substitutions.

#### #10 · Comment 3
**Highlighted:** "not" (in "ranks partners on customer sentiment and honesty, not photo scores")
> Photoscore also is there but just less instead of a high percentage for photoscore it's only 20%

**AI (condensed):** Updated the executive summary to "mainly on customer reviews (40%) and honesty (40%), with photo check results as a smaller 20% share."

#### #11 · Comment 4
**Highlighted:** "HQ > Integrity" (HQ routes table)
> OK from here I'm seeing HQ integrity flag Q reference library AI health calibration I think these are a little bit vague I want you to umm provide a little bit more explanation on the page slash view name

**AI (condensed):** Added an explanation to each HQ page name from Integrity through Settings.

#### #12 · Comment 5
**Highlighted:** the Integrity flag queue explanation
> OK you went a little bit overboard here I would say don't use that many words like for the explanation keep it within 10 words

**AI (condensed):** Cut all seven HQ page explanations to 10 words or fewer.

#### #13 · Comment 6
**Highlighted:** "Monthly vendor review — AI-drafted, human-approved summary of a vendor's month"
> I don't think it's should be human approved summary of the vendors month I think they should just be completely AI but the summary is not off the AI judge dishes it should be in summary of their vendors integrity combined with the user end user so it's the consumers grade in stars combined, Remember the 8080 20 score, still keep this one under ten words

**AI (condensed):** Renamed to "AI summary: customer star ratings + integrity, 40/40/20 score." Rewrote Feature 13 as a fully AI-generated summary of the vendor's reliability, not of individual dish judgments, using only integrity flags a reviewer already confirmed.

#### #14 · Comment 7
**Highlighted:** the honesty deductions table
> I want you to add more less major deductions over here like if we detected multiple retakes to pass a test we need to use a minor deduction, Or repeated attempts without any clarification on retaking images that also needs to do a minor deduction and change the retake that swaps in a different dish or stage dish to a minor and add maybe one or two more minor deductions of confirmed behavior.

**AI (condensed):** Downgraded "retake that swaps in a different or staged dish" to Minor. Added Minor deductions for needing 4+ retakes to pass, repeated retakes with no clarification, a pattern of disputes rejected as unfounded, and Today's Notes that repeatedly don't match the dish.

---
#### #15 · Export the PRD conversation
> OK I just worked through the entire thing It looks really good. Now I want you to export the entire dialog that we have made so your AI quality cockpit with PRD is past and we are creating part two of the AI prompt log. I want you to put this in an MD as well and I want you to drop all of the Files attachments and keep it simple.

**AI (condensed):** Wrote Part 2 of the prompt log in Markdown, with my prompts verbatim, its replies summarized and the attachments dropped.

---

### Phase 4 — Choosing how to build the prototypes

#### #16
> OK now I am moving towards a high fidelity web prototype I actually want to use Web UI code and I will your document into this because I believe that is what they want me to use like cursor To create an interactive web page. I want to have as little intervention as possible but have a final say on the design I want you to be extremely brief this time, Just tell me what is the right pipeline for me to load everything that I have created For the best looking AI created Interactive web page

**AI (condensed):** Suggested v0.dev to design the screens, Vercel to share them, and Cursor only for extra logic, with every prompt logged.

#### #17
> Before you start doing that what is V0.dev and why are you only recommending cursor as an additional item can I not just use cursor instead of V0.dev

**AI (condensed):** Explained both tools and compared effort, live preview and control. Cursor alone works too; v0 had come first only because I'd asked for minimal intervention.

#### #18
> OK is it paid Be very brief

**AI (condensed):** Both have free tiers. Paid plans are about $20 a month.

#### #19
> I see what V0 can use ChatGPT plan is there a similar application where I can use my Gemini or my premium Claude plan So I don't have to pay for another subscription

**AI (condensed):** Proposed building the prototypes right in this chat with my existing Claude plan, and named Claude Code and Google AI Studio as alternatives.

#### #20
> Give me a pros and con list between you ,Claude and v0

**AI (condensed):** Pros and cons for each:
- **Claude:** knows the PRD in depth and can connect every screen into one flow, but has no live visual editor.
- **v0:** polished look out of the box, but starts with no context and costs credits.

It recommended building in Claude.

#### #21 · Test photos
> You actually have all of the information that you will need for creating this Web app. Remember there is two different versions one for the Restaurant One our internal use. I want you to create two separate apps with interactive Elements that is exactly designed to the PRD. Do not start creating now I will provide you with all the images that you need from Gemini. I am thinking for example the images that you will need will be the images that we take like a example image of bad image quality and an image with a color card on the side imagine all of the images that you would need to create this mock version of the website And describe it one by one so I can paste it into my Gemini to generate. So we have to go through all of the edge cases of bad photos taken images of fake food Images of broccoli that is green and broccoli that is not and images that are less saturated versus more saturated and images that are using green bell pepper versus yellow or red bell pepper in a ratatouille. Don't do too many images I cannot generate all of them but give me every image that you could need for a good website demo that you will build. So when you are taking a picture or when the user gets prompt to take the picture you branch out to a different menu where you select the images and then it goes to different outcomes to correspond with your flow chart. Give me each of those images prompts so that I can paste it into Gemini for generation

**AI (condensed):** Wrote 12 Gemini prompts in a consistent style. There were two reference dishes, plus ten kitchen photos, each mapped to an outcome:
- red and yellow peppers
- a deeper container
- a color card
- oversaturated and dull phones
- yellow broccoli
- a hair
- a blurry photo
- a photo of a screen
- plastic food

#### #22
> OK I want you to also add the instruction of labeling the image each individually either in the name or as a small tag on the bottom into the prompt for each of the generated photos

**AI (condensed):** Added a short label tag to every prompt, matching its file name.

---

### Phase 5 — The kitchen prototype

#### #23
> OK So I have created all of the images and every single one of them is tagged appropriately on the image itself. I want you to try your absolute best and Craft first the restaurant side, chef side app, make sure to use these images so that we can select the image instead of taking a live image and then feed it through the app and all of the judgment program does not have to be live AI it just have to be a mock up of it. Each of the images should be tagged and automatically Run through a script that is Maybe show what the AI would have said. And make this into a web page that I can just open on my web browser in a phone aspect ratio.

**AI (condensed):** Built the chef app as a phone-sized web page with these screens:
- onboarding
- Today's Notes
- capture, with a picker of my test photos
- Pass / Question results
- a dispute tracker
- a safety hold
- an always-on Help button
- records

Also added a demo panel and one-tap scenarios, and drew a stand-in photo for the hair image, which hadn't come through.

#### #24 · My first review of the kitchen app
> I'm gonna note a few things that I have found. When I click the send message under the help box I can compose my own message and I send it but the send button does nothing I don't think that's a problem but when you click send I think it should pop up a window saying that this is a demo version if you click send the AI LLM will respond with a message or like Maria from We Box Quality team will respond when she is online or any other quality assurance or any other quality assurance. And in a lot of the sections where you are building the app like for example in the rubric section you don't have to explain yourself like every result is a pass or a question with a reason that is not something end user need to see so anything like that I would say try to remove it beyond the very beginning the first startup screen when you have to explain it. Also remove the never judges part that is extraneous and not needed in the rubric. And then I'm looking at the intro again I don't like your line where it says a second pair of eyes, never a judge that is a weak first thing you see in the app right It should say welcome to the We box kitchen For whatever this app is called. And then the next point is that we box have a white background with a red hue that is their signature colors so I want you to follow that And the white background makes sense because the white background often is more strained to the eye but is usually easier to read. I also noticed when I am trying to take the photo in the photo taking page the camera shutter button is offset and it doesn't look that great. And then regarding today's orders I want you to you know after you say all clear show the amount of retakes using a very small number on the side of it after you say all clear under it. And I don't like the workflow that you have created for the hair in the rice, because it is potentially a safety issue We don't want the chef to just remove the hair or remove the bug in the rice and just you know send it out anyway we want to suggest them to remake the dish and check the Cleanliness inside their kitchen. It needs to show more urgency. With a different color that is maybe red and flashing. And I also want you to create a scene where there is a false positive of hair in the rice in which it although shows that there is hair in the rice say taking a look however the human Maria right here decided that there is no rice and there is no urgent problem And then after a few seconds bypasses the AI judgment and then let your dish through anyway. That is a very useful metric that we can do that with two adjust for our weak AI or bad AI and also add a log on the bottom showing everything that is sent to the back end. So it is not going to be within the screen but it's gonna be an additional box on the side. So let's say when a picture gets misidentified as a dangerous Order with objects in there, and it's falsely identified where Maria our worker decided that there is no such problem, it logs underneath saying this data has been sent to our main Dashboard as an AI improvement data. And then I want you to further work on that idea of just having this bottom box that shows what is being sent to our server like after every picture it sends maybe you know 4 scores to our server but that will never be seen by the chefs. And then maybe when we take a photo of the screen or plastic fake food it should send things to the server to take notes against the restaurant Or maybe when I repeatedly say it looks fine even though I didn't change anything about it We will send a small Ding on the reputability score. This is going to be a big feature that you are gonna add for this demo So this demo will now show everything not just from the users perspective but also from our server back ends perspective. There is a lot more to add so please take extra attention and take extra time to do this.  I see how you currently have some integrity flags and waiting a reviewer I'm not sure if that is you know very clear what it does For the demo page so I would like you to rework that into another block to the left of the phone that shows everything our server sees and then maybe over there you can add integrity flags that is raised by this current shop that sells these food. And then when the photo seems like it is coming from a screen or from a fake food sample, It currently just shows all pass but I feel like you should add a small text box on the very bottom for pure transparency saying or asking a question saying is this photo accurately reflecting this dish that you are serving up? Do not directly accuse anyone because AIS can still make a mistake but just add a nudge on these severe honesty point deductions. We should not ring alarm bells because that's what human does But add that note for when something serious like that happens. Those are all the problems that I currently see I want you to rebuild this HTML web page to address all of them. I want you to also to speak to me on how you have addressed those problems in the text chat. Expend a lot of effort into doing this as this needs to be perfect. I have not used any formatting when I am giving you all of these instructions but I want you to first formats everything I have said into a list of instructions that you need to take to adjust this app.

**AI (condensed):** Turned my notes into a checklist, then rebuilt the app.
- **Look and copy:**
  - opens on "Welcome to WeBox Kitchen"
  - explanations appear only in onboarding
  - WeBox white and red
  - centered shutter
  - a small retake count on each order
  - a "demo version" popup on Send
- **Hair in the rice:** a flashing red hold with a four-step checklist: set it aside, check the batch, check the prep area, remake. No "pick it out and send."
- **False-alarm scene:** the AI mistakes a sauce drizzle for a hair, Maria releases the hold, and the case is logged as AI-improvement data.
- **Server panel to the left of the phone:**
  - the 40/40/20 vendor score
  - integrity notes on the restaurant
  - the hidden per-criterion scores
  - a feed of every payload sent
- **Screen photos and plastic food:** a gentle question at the bottom of the results, plus automatic −2 dings for behavior patterns.

It also flagged two spots where the app now differed from the PRD.

#### #25 · Bug report
> #12 Small honesty Dings minus two happens automatically you said that but when go and check 0 this is fine on the very bottom I repeatedly tapped that and it did not think that honesty whatsoever. I also want you to make sure that repeatedly tapping it does not stack the honesty score deduction. Make sure that is reflected in the final app and yes you absolutely should update update your PRD to reflect all the changes that we have made in the app

**AI (condensed):** Found the cause: the scenario only opened the camera, so the ding never fired. Made scenario 12 play by itself, so the second "it's fine" costs −2, once. Every Minor ding now applies at most once per pattern per order; a repeat is logged as "already counted." Tested: honesty went 40 → 38 and stayed at 38 on the second run. Updated the PRD to v0.3 to match the app.

---

### Phase 6 — The HQ prototype

#### #26
> OK now I would like you to follow the PRD document exactly as well as you did the kitchen software prototype Create the back end software and make sure you have all of the images as well and make sure you have multiple different restaurants with all of the potential outcomes so one restaurant has been a perfect green light one restaurant has been an amber light and one restaurant is in the needs conversation immediately red light And then maybe add two more restaurants just to round out the whole format and I want you to build this web page to the best of your capability to exactly match everything on the PRD and make everything interactable but on this web page it should be optimized for a browser instead of a phone. What needs to happen is that this browser web page needs To not fill the entirety of the demo as you still want to explain with a block on the side saying why everything is the way it is as you did with the phone app. For example this restaurant has lost a lot of integrity points because it showed a lot of fake photos coming in and if you click verified to be true it is going to take a big hit on the company so the idea is even though if a company have perfect scores otherwise if any one Of the customer reviews criteria or the integrity criteria dips below a threshold maybe let's say 10 This is a mark of and needs review so I would say for one restaurant we just have an overall low score of 60 or below that triggers an automatic review call request on our side and another restaurant have perfect scores otherwise but it have a very low integrity score and then that causes some real issue and that will cause them to get the we need a conversation as well. And as for everything I want you to follow exactly what you have said in the PRD I have approved everything in the PRD and it looks good So go ahead and spend as much time and as much effort as you need to create the perfect website. This back end should look professional and this is a back end designed for within the office so it should be dark themed so that we expect people to be looking at this back end for a very long time And it will be better on their eyes and it's gonna be in less harsh environments than in the kitchen and it will be better on their eyes and it's gonna be in less harsh environments than in the kitchen. Now build this web page.

**AI (condensed):** Built the HQ portal as a dark desktop app, with a demo-notes column explaining every screen.

Six restaurants cover every outcome:
- **Lotus & Thyme:** healthy.
- **Provence Table:** healthy.
- **Bayside:** healthy, but with a live safety hold.
- **Golden Wok:** amber.
- **Harbor Street:** total ≤ 60, so a review call was requested automatically.
- **Sunrise Bento:** 4.8★, but honesty is below 10, so it needs a conversation.

Screens:
- Command Center
- Safety Queue
- Review Queue
- Inspection workspace
- Vendors, with 30-day trends
- Integrity, where "verify as true" shows the hit before it lands
- References
- AI Health
- monthly AI reviews
- Audit log, with server events
- Settings that recompute everything live

It also added the thresholds to the PRD (v0.4).

#### #27 · Test plan
> OK now I won't like you to create a plan of how I would go about testing every feature and every scenario you have built using this website Use simple bullet points and things to do on the button that should be clicking so I can go through all the permutations of the website and seeing what changes so it should be the action I should take and the changes I should see.

**AI (condensed):** Wrote a click-by-click test plan in six runs, each step pairing an action with the change to expect:
1. look around
2. the main story
3. the opposite choices
4. the rules in Settings
5. partner calls
6. window sizes

It also fixed a few labels it caught while writing the plan.

---

### Phase 7 — Rethinking, and the final round

#### #28 · Optional pilot, photo pledge, two HQ roles
> OK you know I'm just thinking about this entire app and why I designed it this way The honesty thing I believe makes having this app as a fully Required thing to be a little wierd. It feels like it is judging the owners of the restaurant and it might be a little Unnecessarily harsh on judging people who just want to game a good score , so I believe this app first of all should be an optional app for the users to use until the AI has been honed in all the way. This app should not be an app that judges The end user harshly based on what they have cooked but it should be an app that's designed for food safety. One note for the started up of the Kitchen side app is creating a pledge where you have to tick to say I pledged that these images of food is of the food that I'm going to send out so it have to be the same. This honesty pledge makes our honesty scoring system Have you know a standing ground so that we Ding the users for something Like dishonesty and trying to game the system. And for the Webox HQ app I would like you to have two 2 different accounts Maria W is a reviewer So the review should only be able to see Command Center open safety holds And review queue. The AI Health tab should be invisible to this person and the final tab where you can adjust all of the settings that should also not be available for this person so the Settings tab should still be there and I would like you to change the icon for the Settings tab to gear but not a sun. All of the AI thresholds and reliability rules should be invisible to Maria. However I want you to create another account Take webox's CEO's name, Fred ming, He should be set as the administrator and when you are the administrator you should be able to have everything available to you so everything you can change. You currently have this little name box on the top with a icon I wanted to change accordingly to the different people. And also I want you to create a fake login page in which when you click login you can switch between the two accounts Maria and Fred. I also want you to first before you start to organize what I just said into a clear list of the things that you need to change both in the Kitchen app and in the HQ app. Everything you have changed also needs to reflect in the PRD accordingly. Make all of these changes right now and I want you to double check it after you make the changes that everything is correct and everything is working properly with the most amount of polish in which you are currently doing great everything looks correct it's just that I have a few things that I can point out like the sun instead of a gear icon small things like that really matter. Take your time and this one of the last if not the last versions you have to make of both of these apps

**AI (condensed):** Listed the changes first, then built them.
- **Kitchen app:**
  - framed as a food-safety check that's optional during the pilot
  - a new last onboarding step: the photo pledge, with "Start service" locked until it's ticked
- **HQ app:**
  - a demo sign-in for Maria Wong (Quality Reviewer) and Fred Ming (Administrator)
  - pages filtered by role
  - Maria's board shows only holds and reviews, with no scores
  - a "for administrators" page for anything else
  - pilot enrollment for Fred
  - a real gear icon
- **PRD:** updated to v0.5.

It flagged one judgment call: integrity notes would be confirmed by the administrator.

#### #29 · Final round
> OK So I agree with what you say Maria should see a little bit more. I think hiding a reliability score of the restaurant is OK because so that there's no bias coming into a restaurant so Maria can judge fairly however I think Maria should also be able to see the integrity notes on top. Make this change, make this PRD Make sure it's updated The kitchen prototype looks fine to me I want you to go through it one last time for quality check and final polish Not that I see anything wrong with it but I want you to look at it with an extra set of eyes. This is what is going out to my boss, I will directly send this to the CEo And I will chat with him about this So this very much needs to be the best work you have ever done. I would like you to create four documents after this the PRD, the HQ prototype the kitchen prototype and another MD document of everything logging the conversation between me and you so the whole conversation log of this we box test assignment chat. I would say skip all of the exports and create a condensed version of all of the conversation records in the very beginning like a super condensed Sparknotes on how I think Like how I asked you what you think and then I talked about how I think about it and then how I express my opinion on your first draft how this is a back and forth back and forth type of thing And my method of collaboration with you. They would want to see that. And then last but not least I want you to create two scripts that I can work from in brief bullet point format of the two questions of the part four of this assignment part four of this assignment. Resolve critical safety issue in five minutes and how we treat with false positives, from what I have previously said I feel like the answer should write themselves for these questions remember the essence of what I'm trying to build here is a quick response system for customer safety and I wanted to be human centric and respectful to everyone involved. Go ahead and draft those prompts and I will edit them and tell you exactly what I want you to change about them.

**AI (condensed):**
- **Maria and integrity notes:** Maria now sees integrity notes and verifies or dismisses them **blind**. She sees the photo, the evidence, the chef's answer and the pledge, but never the score or what her decision does to it. Fred sees the same, plus the score effect.
- **Final quality pass on the kitchen app:** every scenario was walked through, and these were fixed:
  - onboarding steps now open at the top
  - the supervisor's initials now match HQ
  - the pledge shows its date
  - the Help assistant now names food safety first
- **HQ:** re-tested under both accounts.
- **Delivered:**
  - the PRD (v0.5)
  - both prototypes
  - this log
  - the two Part 4 scripts

---

*Left out on purpose: file contents, code, tool output and exported documents. Prompt Log Part 2 (`WeBox_AI_Prompt_Log.md`) holds the earlier, PRD-only version of this record.*
