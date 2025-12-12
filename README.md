# The "Ethics First" Counterfactual Audit of Google's Youtube Kids
## Impact Assessment
### Incident: Google's Youtube Kids App Presents Inappropriate Content

### Who were the subjects?
- Children who have been exposed to inappropriate content via Youtube Kids are the ones most at risk. Parents and families are also affected because they thought Youtube was safe and reliable in terms of providing adequate content to kids. Parents and advocacy groups have pressured Youtube which is also affected as they face criticism and advisor concerns. 

### What is the problem 
- Children are still being exposed to inappropriate content despite parent concerns.
- Youtube Kids was marketed as a safe app for children engagement but they have failed to maintain the app safe for children. 

### Where are people encountering this problem?
- This problem is seen anywhere where Youtube Kids is available. 

### Why is it a problem?
- Children may continue to be exposed to inappropriate content which can negatively affect their development and safety. Solving this problem would mostly benefit children who would gain a safer media environment. It would also help regain parent trust and their peace of mind. Youtube would benefit from a solution by not having anymore advertisers pull out of the platform because their ads were attached to hateful content. 

## The "Washington" Test

### Did this model predict a behavior, or did it predict a proxy?
The intended behavior of this model was to show only safe, age appropriate children's content. Instead, the model predicted videos that look like children's content instead of videos that are safe for kids. It predicted a proxy instead of a behavior because it assumes that characters such as Elmo or Elsa are automatically a video safe for kids. 

### Was this prediction truly in the "Public Interest"?
Youtube only responded to concerns after advertisers became concerned. Parent's concerns alone did not drive major change. This indicates that corporate incentives were more of a priority rather than public welfare. They have  failed to be responsive to the public’s demands so no predictions were not made in the Public Interest. 

##  Classifying the failure using the Common Ethical Pitfalls

### Automation Bias: 
Automation bias is the human tendency to over rely on automated systems and assume they are correct even when they are wrong. In this case it initially played a role because moderators or designers assumed that the AI classifier was correctly filtering out harmful content. Parents also assumed that youtube kids were safe due to its marketing. 
- Example : Moderators may have trusted the AI classification without cross checking. Similarly parents assumed the platform's marketing guaranteed safety. The result of this automation bias was that inappropriate videos were rarely reviewed allowing harmful content to slip through. 

### Feedback Loop 
Feedback loop is when a system's outputs reinforce its own predictions or biases which lead to amplifying errors over time. In this case this was likely the strongest failure because if children briefly interacted with borderline content such as cartoon-looking videos with inappropriate content, the system interpreted this as engagement and further reinforces it by recommending similar videos to that one. 
- Example : If a child clicked on one inappropriate video without realizing, the recommendation engine interpreted this as a positive engagement so it created a loop that promoted more inappropriate videos. 

## The Data Anatomy : Bias vs Noise 

Bias is the average error in predictions. It is a systematic error, a consistent directional mistake. 

Noise is the random, irrelevant fluctuations in data or judgements creating variability. It is unreliable and inconsistent in judgement. 

### Was the error caused by System Noise (unwanted variability in judgments, e.g., different human labelers giving different answers) or Predictive Bias (systematic error in one direction)?
This error was caused both by system noise and predictive bias. 

#### Predictive Bias
Youtube's algorithm was systematically biased toward promoting content that looked like children's content even if it was unsafe. It learned from wrong proxy signals such as keywords and character names because it was optimized for engagement not safety. The system was designed a certain way which allowed it to make the same mistakes over and over again.  

#### System Noise
System noise here is the inconsistent human judgement during data labeling or moderation. The two major types found are occasion noise and system noise. Occasion noise happens when the same moderator is inconsistent with themselves. This is prone to happen as reviewers become fatigued after reviewing hundreds of videos leading to errors in their judgment. After reviewing many violent videos a borderline video may not seem as bad even if it is. System noise happens when different moderators have different judgements. There is an inconsistent definition of inappropriate videos which leads to label noise in the training set. 


## Data Protection & Privacy 

### Retroactive Data Card 

#### 1. Data Origin & Purpose 
##### Intended Purpose 
To build: 
- Content filtering models for Youtube Kids
- Recommendation models for children safe browsing
- Safety classifiers trained on human-labeled "appropriate/inappropriate" videos
- Search ranking and recommendation rules based on engagement data from children and their parents

#### Actual Use 
The data was used to : 
- Train ML systems that filter videos before entering the Youtube Kids App
- Power a "Recommended for you" engine inside the app
- Drive "trending" and "popular" lists
- Serve targeted and contextual ads in the Kids app

### 2. Data Collection 
#### Sources of Data 
- User interaction logs from children such as clicks, watch duration, and search history
- Metadata from characteristics such as titles, thumbnails, and tags
- Transcripts, audio and visual frames from videos
- Parent account settings and controls
- Content flagged by parents or others
- Human-labeled moderation dataset created by Youtube employees, third-party contractors and/or community flagging

#### Notable Properties 
- Enormous Scale : "400 hours of new content per minute"
- Wide Cultural Inconsistency : "Global Contributors"
- Highly adversarial environement: Creators manipulate thumbnails and titles to bypass filters"

### 3. Labeling Process 
#### Human Labelers 
- Moderation contractors (globally distributed)
- Youtube internal trust and safety staff
- Community flagging by parents and viewers 

### Issues Identified
#### System Nose 
- Inconsistent judgements across reviewers
- Variable strictness thresholds
- Wide range of reviewer exposure effects (occasion noise)
- Shifting norms as bad actors invent no formats

#### Adversarial Manipulation 
- Creators use misleading thumbnails to bypass moderation
- Videos mimick popular kids aesthetics to appear safe

-> these inconsistencies contaminate the training data 

### 4. Modeling & Deployment 
#### Model Types Used 
- Video Classification (safe vs inappropriate)
- Thumbnail/Title Classification
- Text Transcript Classification
- Recommendation and Ranking algorithms which used: engagement data, search behavior, and viewing history

#### Model Failures 
- Allowed videos that mimic kids content but contain violence/sexual content
- Recommended increasingly inappropriate content after a child clicked one borderline video
- Removing flagged videos did not prevent new variants from appearing

#### Why did these failures happen? 
- Label noise due to inconsistent human moderation
- Engagement optimized recommendation system amplified borderline videos
- Adversarial creators exploiting metadata/thumbnails
- Overreliance on automation (automation bias) by parents and Youtube
- Inadequate human oversight relative to content volume

### 5. Harms 
#### Direct Harms 
- Exposure of children to sexual content, violence, profanity and unsafe behavior
- Increased risk of developmental harm
- Manipulation of children through commercial content

#### Indirect Harms 
- Erosion of parent trust
- Spread of harmful content
- Reputation and advertiser safety crisis

### 6. GDPR/ Privacy Check 
#### Was there a privacy violation even if the model had worked perfectly?
Even if no inappropriate content ever slipped through the filters, YouTube Kids’ data practices likely violate GDPR due to:
- profiling minors
- insufficient parental consent
- excessive behavioral data collection
- non-transparent secondary uses (ads, ranking, engagement optimization)

## The Framework Shutdown 
### At what stage of the AI Project Cycle did the failure occur? 

The primary failure points were: 
1) Problem Scoping - Youtube underestimated the adversarial ways the system could be exploited
2) Data Acquisition - Harmful content was included in the dataset and not properly labeled or filtered
3) Data Exploration - Early warning signals in the data were not detected, audited or addressed
-> Modeling, Evaluation and Deployment failed because the scoping and data were weak




### Proposed Fix 
Proposal: Parents can create a kids library that has no recommendations ; only preselected videos appear.  

#### The Utilitarian Argument 
Implementing a parent controlled kids library maximizes overall well-being by minimizing children’s exposure to harmful content. 
- By removing algorithmic recommendations, the system enhances reliability and security by limiting exposure to potentially harmful or inappropriate content. 
- This approach improves transparency and accountability as parents know exactly what content their children can access, building trust with the platform. 
- It supports privacy by empowering parents to control content without excessive collection or intrusive profiling 
- It reduces societal harm by increasing safety and peace of mind for families, the net benefit is greater because children are safer and parents are more confident, the platforms would also be protected from backlash. 
- This design reflects responsible use of AI by avoiding over-reliance on imperfect algorithms in sensitive contexts. 

#### The Kantian Argument 
Implementing a parent-controlled kids library is a categorical imperative because it protects children and families.
- There is accountability and transparency by ensuring parents play an active role in their children’s media exposure. 
- This implementation would prevent exploitation by algorithmic engagement tactics that treat viewers as means to revenue. 
- By prioritizing privacy and security, the system safeguards vulnerable users from invasive profiling or unpredictable content. 
- Children’s well being and parental control are not compromised for efficiency or profit. 

## The Technical Safeguard & XAI 
### The Ethical Design Proposal 
Proposal: Implement a human-gated recommendation filter (HGRF) : a system in which any video eligible for Youtube Kids must pass through. 
If a video does not pass the following three steps, it cannot appear in Youtube Kids or recommendations: 
1. Algorithmic Safety Screening ( violence, impersonation, sexual content etc) 
2. Explainable AI Scoring Layer (Shap-Lime based)
3. Final approval would be the human review gate before recommendations are allowed.

### Where would have the "Ethics First" check stopped in the orginal timeline? 

```
+------------------------------+
|      1. Problem Scoping      |
+--------------+---------------+
               |
   ⚠️ FAILURE: Risks underestimated
   - Adversarial content not considered
   - Definition of "child-safe" unclear
               |
               v
+------------------------------+
|      2. Data Acquisition     |
+--------------+---------------+
               |
   ⚠️ FAILURE: Data not filtered
   - Harmful videos included in dataset
   - No adversarial labeling
               |
               v
+------------------------------+
|      3. Data Exploration     |
+--------------+---------------+
               |
   ⚠️ FAILURE: Edge cases ignored
   - Patterns of exploitative content missed
   - No stress-testing of "kid-bait" videos
               |
               v
+------------------------------+
|          4. Modeling         |
+--------------+---------------+
               |
   ⚠️ IMPACTED: Algorithm trained on bad data
   - ML models learned from harmful content
   - Lack of human-in-the-loop safeguards
               |
               v
+------------------------------+
|         5. Evaluation        |
+--------------+---------------+
               |
   ⚠️ IMPACTED: Evaluation reactive, not proactive
   - Human reviewers only partially effective
   - No systematic adversarial testing
               |
               v
+------------------------------+
|         6. Deployment        |
+--------------+---------------+
               |
   ⚠️ IMPACTED: Harmful videos reached children
   - Moderation gaps
   - Recommendations exposed kids to unsafe content
               |
               v
+------------------------------+
|   Post-Deployment Feedback   |
|            Loop              |
+------------------------------+
   - Parents and advocacy groups flagged content
   - Feedback used, but only after widespread exposure
```
** This graph was AI generated 


### How are Explainability and Ethical Design embedded throughout the AI lifecycle? 


```
+------------------------------+
|      1. Problem Scoping      |
+--------------+---------------+
               |
   ✅ Define child-safety as primary objective
   ✅ Include adversarial scenarios
   ✅ Ethical Design: prioritize wellbeing over engagement
               |
               v
+------------------------------+
|      2. Data Acquisition     |
+--------------+---------------+
               |
   ✅ Curate labeled dataset
   ✅ Exclude unsafe or exploitative videos
   ✅ Include adversarial examples for robust training
               |
               v
+------------------------------+
|      3. Data Exploration     |
+--------------+---------------+
               |
   ✅ Detect harmful patterns & edge cases
   ✅ Use Explainable AI to audit data
   ✅ Ethical Design: identify bias, unsafe trends
               |
               v
+------------------------------+
|          4. Modeling         |
+--------------+---------------+
               |
   ✅ Algorithmic Safety Screening (HGRF Step 1)
   - Detect violence, sexual content, impersonation, unsafe behavior
   ✅ Explainable AI Scoring Layer (HGRF Step 2)
   - SHAP / LIME scoring for transparency
               |
               v
+------------------------------+
|         5. Evaluation        |
+--------------+---------------+
               |
   ✅ Human Review Gate (HGRF Step 3)
   - Manual approval required before recommendations
   ✅ Red-team testing & stress-test for adversarial videos
   ✅ Ethical Design: ensures context-aware, child-safe decisions
               |
               v
+------------------------------+
|         6. Deployment        |
+--------------+---------------+
               |
   ✅ Only videos passing HGRF are recommended
   ✅ Live monitoring for drift & new adversarial content
   ✅ Explainability dashboards for moderators and parents
               |
               v
+------------------------------+
|   Post-Deployment Feedback   |
|            Loop              |
+--------------+---------------+
               |
   ✅ Continuous collection of flagged content & parent feedback
   ✅ Update models and rules using Explainable AI insights
   ✅ Transparent reporting & accountability
```
** This graph was AI generated 

### The XAI Requirement 
How would SHAP values, LIME, or Counterfactual Explanations have allowed a human operator to catch this error before it caused harm?"

- SHAP would have shown features the model relied on when deciding a video was child appropriate. It would show that the model is making the wrong decision for the wrong reasons.

- LIME would highlight local explanations frame by frame. Lime would reveal the local inconsistency that algorithms alone could not detect.
  Humans reviewers would see “normal looking intro frames classified as safe” or “violent or disturbing frame misclassified as toys” 


### Explanation Interface 

The goal of this interface is to: 
1) Provide transparent explanations of the models decision
2) Show global SHAP feature contributions (why this model thinks the video is "safe")
3) Show local LIME explanations (frame-by-frame safety analysis)
4) Allows a reviewer to override bad model decisions
5) Create an audit train that would have prevented inappropriate content from appearing on Youtube Kids


```
┌───────────────────────────────────────────────────────────────┐
│                 YOUTUBE KIDS — SAFETY REVIEW UI               │
├───────────────────────────────────────────────────────────────┤
│ VIDEO PREVIEW                                                  │
│ ┌───────────────────────────────────────────────────────────┐ │
│ │                      [ Thumbnail Preview ]                │ │
│ └───────────────────────────────────────────────────────────┘ │
│ Title: Peppa Pig Playtime (Funny!)                             │
│ Uploader: KidsFunChannel123                                     │
│ Model Risk Score: 0.71   →   FLAGGED FOR HUMAN REVIEW           │
├───────────────────────────────────────────────────────────────┤
│ GLOBAL EXPLANATION — SHAP VALUES                               │
│ (What features influenced the model's decision overall?)        │
│                                                                 │
│   +0.42   Bright, high-saturation thumbnail colors              │
│   +0.31   Cartoon-like character detection                      │
│   +0.19   Child voice in first seconds                          │
│   -0.12   Screaming audio at 01:23                              │
│   -0.18   Distorted face detection (frames 214–230)             │
│   -0.21   Violent action cluster detected                       │
│                                                                 │
│ Reviewer Insight:                                               │
│ → Model is over-weighting "childish" aesthetics.               │
│ → Harmful audiovisual features are being minimized.             │
├───────────────────────────────────────────────────────────────┤
│ LOCAL EXPLANATION — LIME FRAME ANALYSIS                        │
│ (Which exact frames influenced the model’s decision?)           │
│                                                                 │
│   Timestamp       Model Judgment       Reason                   │
│   -----------------------------------------------------------   │
│   00:00–00:03     [ SAFE ]             Cartoon intro detected   │
│   01:23–01:27     [ RISK ]             Screaming + distorted face│
│   02:10–02:15     [ RISK ]             Violent movement detected │
│   02:15–02:45     [ SAFE ]             Bright toy colors         │
│                                                                 │
│ Reviewer Insight:                                               │
│ → Mid-video unsafe segments contradict intro safety cues.       │
│ → Model incorrectly judged video as safe due to intro + colors. │
├───────────────────────────────────────────────────────────────┤
│ ACTIONS                                                         │
│                                                                 │
│   [ REJECT FOR YOUTUBE KIDS ]   (remove + record justification) │
│   [ ESCALATE TO SENIOR REVIEW ]  (uncertain or borderline)      │
│   [ APPROVE ]                  (fully safe)                     │
│   [ FLAG FOR RETRAINING DATASET ] (use this example to improve) │
└───────────────────────────────────────────────────────────────┘
```
** This wireframe was AI generated

### Explanation 
The interface above demonstrates how explainability tools would have prevented the Youtube Kids failure. 

First, SHAP would reveal systemic misclassification. The panel shows that the model relied too heavily on bright colors, cartoon shapes, and child-like voices which are things that creators can easily manipulate. This shows that the model is making the wrong decisions for the wrong reasons. Then, LIME would expose harmful frames. The LIME frame-by-frame breakdown highlights specific timestamps where things like screaming audio , distorted faces, and violent motions were present. These were things that the model incorrectly minimized. Lastly,the overviewer would see contradictory SHAP/LIME evidence so they would reject the video, preventing the video from entering the kids app. They could then add it to retraining data in hopes of fixing the model.  





Works Cited : 
- OpenAI. ChatGPT, version 5.1, OpenAI, 2025, https://chat.openai.com/.
- “Incident 1: Google’s YouTube Kids App Presents Inappropriate Content.” AI Incident Database RSS, incidentdatabase.ai/cite/1/. Accessed 11 Dec. 2025. 




