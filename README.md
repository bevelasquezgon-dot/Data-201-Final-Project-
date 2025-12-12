# THe "Ethics First" Counterfactual Audit 

## Impact Assessment
### Incident: Google's Youtube Kids App Presents Inappropriate Content

### Who were the subjects?
- Children have been exposed to inapproriate content via Youtube Kids, drawing concern to parents. Parents are concerend for their children's exposure to these things. 

### What is the problem 
- Children are still being exposed to inappropriate content despite parent concerns.
- Youtube Kids was marketed as a safe app for children engagement but they have failed to maintain the app safe for children. 

### Where are people encountering this problem?
- This problem is seen globally, anywhere where Youtube Kids is available. 

### Why is it a problem?
- Youtube Kids was marketed as a safe app for children engagement but they have failed to maintain the app safe for children. 

### Did this model predict a behavior, or did it predict a proxy?
This model predicted a proxy instead of a behavior because it assumes that characters such as Elmo or Elsa are automatically a video safe for kids. 

### Was this prediction truly in the "Public Interest"?
Youtube has failed to recognize their flaws and they have even stated that it is the parents fault. They have  failed to be responsive to the public’s demands so no predictions were not made in the Public Interest. 

##  Classifing the failure using the Common Ethical Pitfalls

### Automation Bias: 
Automation bias is the human tendency to over rely on automated sytems and assume they are correct even when they are wrong. In this case it initially played a role because moderators or designers assumed that the AI classifier was correctly filtering out harmful content. Parents also assumed that youtube kids were safe due to its marketing. 
- Example : Moderators may have trusted the AI classification without cross checking. Similarily parents assumed the platform's marketing guaranteed safety. The result of this automation bias, nappropriate videos were rarely reviewed allowing harmful content to slip throught. 

### Feedback Loop 
Feedback loop is when a system's outputs reinforce its own predictions or biases which lead to amplifying errors over time. In this case this was likely the strongest failure because if children briefly interacted with borderline content such as cartoon-looking videos with inappropriate content, the system interpreted this as engagement and further reinforces it by recommending similar videos to that one. 
- Example : If a child clicked on one borderline video, the recommendation engine interpreted this as a positive engagment so it created a loop that promoted more inappropriate videos. 

## The Data Anatomy : Bias vs Noise 

Bias is the average error in predictions. It is a systematic error, a consistent directional mistake. 

Noise is the random, irrelevant fluctuations in data or judgements creating variability. It is unreliable and inconsistent in judgement. 

### Was the error caused by System Noise (unwanted variability in judgments, e.g., different human labelers giving different answers) or Predictive Bias (systematic error in one direction)?
The failures in Youtube Kids are primarily caused by System Noise, especially Occasion Noise and inter-labeler variability during training-label creation which leads to inconsistent and incorrect judgements. 
Predictive Bias is a result of the overly permissive rules from these noisy labels. EX: training bright colored thumbnails as safe .

## Data Protection & Privacy 

### Retroactive Data Card 

#### 1. Data Origin & Purpose 
##### Intended Purpose 
To build: 
- Content- filtering models for Youtube Kids
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
- Metadata from crates such as titles, thumbnails, and tags
- Transcripts, audio and visual frames from videos
- Parent account settings and controls
- Content flagged by parents or others
- Human-labeled moderation dataset created by Youtube employees, third-party contracors and/or community flagging

#### Notable Properties 
- Enormous Scale : "400 hours of new content per minute"
- Wide Cultural Inconsistency : "Global Contributers"
- Highly adversarial environemnt: "creaters manipulate thumbnails and titles to bypass filters"

### 3. Labeling Process 
#### Human Labelers 
- Moderation contractors (globally distributed)
- Youtube internal trust and safety staff
- Community flagging by parents and viewers 

### Issues Identified
#### System Nose 
- Inconsistent judgements across reviewers
- Variable strictness threshilds
- Wide range of reviwer exposure effects (occasion noise)
- Shifting norms as bad actors invent no formats

#### Adversarial Manipulation 
- Creators use misleading thumbnails to bypass moderation
- Videos mimick popular kids aesthetics to appear sage

-> these inconcistencies contaminate the training data 

### 4. Modeling & Deployment 
#### Model Types Used 
- Video Classification (safe vs inappropriate)
- Thumnail/Title Classification
- Text Transcrip Classification
- Recommendation and Ranking algorithms which used: engagement data, search behavior, and viewing history

#### Model Failures 
- Allowed videos that mimic kids content but contain violence/sexual content
- Recommended increasingly inappropriate content after a child clicked one borderline video
- Removing flagged videos did not prevent new varients from appearing

#### Why did these failures happen? 
- Label noise due to inconsistent human moderation
- Engagment optimized recommendation system amplified borderline videos
- Adversarial creaters exploiting metadata/thumbnails
- Overreliance on automation (automation bias) by paretns and Youtube
- Inadequente humuan oversight relative to content volume

### 5. Harms 
#### Direct Harms 
- Exposure of children to sexual content, violence, profanity and unsafe behavior
- Increased risk of developmental harm
- Manipulation of children through commerical content

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
The failure occurred primarily in the deployment stage of the ai project cycle. 
The problems emerged after the Youtube kids app and its recommendation algorithms were released for use. Harmful and misleading content slipped through the live recommendation system because bad actors exploited the operational algorithm after launch. The app and algorithms were functional but they underperformed in the wild. 

### Proposed Fix 
Proposal: Parents can create a kids library that has no recommendations ; only preselected appear.  

#### The Ulitarian Argument 
Implementing a parent controlled kids library maximizes overall well-being by minimizing children’s exposure to harmful content. 
- By removing algorithmic recommendations, the system enhances reliability and security by limiting exposure to potentially harmful or inappropriate content. 
- This approach improves transparency and accountability as parents know exactly what content their children can access, building trust with the platform. 
- It supports privacy by empowering parents to control content without excessive collection or intrusive profiling 
- It reduces societal harm by increasing safety and peace of mind for families, the net benefit is greater because children are safer and parents are more confident, the platforms would also be protected from backlash. 
- This design reflects responsible use of Ai by avoiding over-reliance on imperfect algorithms in sensitive contexts. 

#### The Kantian Argument 
Implementing a parent-controlled kids library is a categorical imperative because it protects children and families.
- There is accountability and transparency by ensuring parents play an active role in their children’s media exposure. 
- This implementation would prevent exploitation by algorithmic engagement tactics that treat viewers as means to revenue. 
- By prioritizing privacy and security, the system safeguards vulnerable users from invasive profiling or unpredictable content. 
- Children’s well being and parental control are not compromised for efficiency or profit. 

## The Techinical Safeguard & XAI 
Proposal: Implement a human-gated recommendation filter (HGRF) : a system in which any video eligible for Youtube Kids must pass through. 
If a video does not pass all three steps, it cannot appear in Youtube Kids or recommendations: 
1. Algorithmic Safety Screening ( violence, impersonation, sexual content etc) 
2. Explainable Ai Scoring Layer (Shap-Lime based) 
3. Final approval would be the human review gate before recommendations are allowed. 

** Diagram Here (Getty Images) 

                    ┌──────────────────────────────┐
                    │      1. Problem Scoping       │
                    └───────────────┬──────────────┘
                                    │
                                    ▼
                    ┌──────────────────────────────┐
                    │      2. Data Acquisition      │
                    └───────────────┬──────────────┘
                                    │
                     ETHICS-FIRST CHECKPOINT #1
           - Privacy Assessment (GDPR / minors’ data)
           - Bias & Noise Audit (labeler variability)
           - Data Minimization + Purpose Limitation
                                    │
                                    ▼
                    ┌──────────────────────────────┐
                    │      3. Data Exploration      │
                    └───────────────┬──────────────┘
                                    │
                     ETHICS-FIRST CHECKPOINT #2
        - Detect label noise, adversarial patterns, 
          cultural inconsistency, and content manipulation
                                    │
                                    ▼
                    ┌──────────────────────────────┐
                    │          4. Modeling          │
                    └───────────────┬──────────────┘
                                    │
                     ETHICS-FIRST CHECKPOINT #3
         - XAI Layer Added (SHAP/LIME/Counterfactuals)
         - Human Approval Gate for “child-safe” classifier
         - Safety Thresholds, Auditability, Transparency
                                    │
                                    ▼
                    ┌──────────────────────────────┐
                    │         5. Evaluation         │
                    └───────────────┬──────────────┘
                                    │
                     ETHICS-FIRST CHECKPOINT #4
       - Reviewer sees model explanations BEFORE release
       - Stress-test with adversarial kid-bait content
       - Red-team harmful video variations
                                    │
                                    ▼
                    ┌──────────────────────────────┐
                    │         6. Deployment         │
                    └───────────────┬──────────────┘
                                    │
                     ETHICS-FIRST CHECKPOINT #5
      - Live Monitoring for drift, new adversarial trends
      - Human-Gated Recommendation Filter (HGRF)
      - Escalation pipeline for parent flagging
                                    │
                                    ▼
                    ┌──────────────────────────────┐
                    │       Post-Deployment         │
                    │        Feedback Loop          │
                    └──────────────────────────────┘





### The XAI Requirement 
How would SHAP values, LIME, or Counterfactual Explanations have allowed a human operator to catch this error before it caused harm?"

- SHAP would have showed features the model relied on when deciding a video was child appropriate. It would show “ the model is making the wrong decision for the wrong reasons” 

- LIME would highlight local explanations frame by frame. Lime would reveal the local inconsistency that algorithms alone could not detect.
  Humans reviewers would see “normal looking intro frames classified as safe” or “violent or disturbing frame misclassified as toys” 


** Mock up an "Explanation Interface" (wireframe or diagram) that shows what the operator should have seen 

### Explanation Interface 

The goal of this interface is to: 
1) Provide transparant explanations of the models decision
2) Show global SHAP feature contributions (why this model thinks the video is "safe")
3) Show local LIME explanations (frame-by-frame safety analysis)
4) Allows a reviewerd to override bad model decisions
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

### Explanation 
The interface above demonstrates how explainability tools would have prevented the Youtube Kids failure. 
First, SHAP would reveal systemic misclassifaction. The panel shows that the model relied too heavily on bright colors, cartoon shapes, and child-like voices which are things that creators can easily manipulate. This shows that the mdoel is making the wrong decisions for the wrong reasons. 

Then, LIME would expose harmful frames. The LIME frame-by-frame breakdown highights specific timestamps where things like screaming audio , distorted faces, and violent motions were present. These were things that the model incorrecly minimized. 

Lastly,the overviewer would see contradictory SHAP/LIME evidenence so they would reject the video, preventing the video from entering the kids app. They could then add it to retraining data in hopes of fixing the model.  




Works Citied : 
OpenAI. ChatGPT, version 5.1, OpenAI, 2025, https://chat.openai.com/.
“Incident 1: Google’s YouTube Kids App Presents Inappropriate Content.” AI Incident Database RSS, incidentdatabase.ai/cite/1/. Accessed 11 Dec. 2025. 




