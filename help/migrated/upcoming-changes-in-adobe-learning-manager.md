---
title: Adobe Learning Managerの新機能
description: Adobe Learning Managerで予定されている変更をご確認ください。 最新のアップデートや今後の発表に関する情報の受け取りを希望します。
exl-id: 4d2129c4-42d8-446f-8837-879b5c2f42bf
source-git-commit: 4a4c42968caf6c0c8265014d99a2211da4c1cbb9
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Adobe Learning Managerのアップデート

[2026年4月リリース](/help/migrated/whats-new.md)がリリースされました。 現時点では、今後の追加変更はありません。 このページは、新しいお知らせが利用可能になったときに更新されます。

<!-- 
>[!IMPORTANT]
>
>The features in this release are available in beta. Functionality and behavior may change before general availability. Share feedback through your usual Adobe support channels.


This document summarizes the new features, improvements, and updates in the April 2026 release of Adobe Learning Manager. Use it to plan changes for your organization and understand what's available for learners, administrators, and authors.

**For learners:** The Fluidic Player now shows the next module name and a clear Exit button. Player language can be set via LTI for a consistent experience across platforms. Captivate content includes a unified table of contents, slide-level completion ticks, and reliable notes exports. Multi-language support is available for Job Aids, checklist questions, and video text tracks (VTT). The AI Assistant helps learners get answers within the learning experience.

**For administrators and authors:** The Zoom Connector supports multiple concurrent VILT sessions. Shared courses in peer accounts display the real author instead of "External Author." Admins can restrict when modules can be started. Learning Object expiry dates are exposed in Learner APIs. Checklist modules support weighted scoring, multilingual question text, and optional reviewer comments. Custom certificates offer a drag-and-drop editor with dynamic fields and AI-generated backgrounds. The non-logged-in Experience Builder lets you build public learning pages without requiring login.

**For instructors:** Generate QR codes for instance enrollment and session attendance. Add comments or feedback during checklist evaluation.

**Reporting and analytics:** SCORM content can now report multiple quiz attempts in L2 reporting. Learning time spent calculation is improved in Learner Transcripts. Learning Transcript reports for Administrators are updated. Advanced search enhancements are available.

## Fluidic Player navigation: show the name of the next module 

### Overview

This enhancement was already included in the November 2025 release of Adobe Learning Manager. 

The "Next" action in the player indicates what will happen when clicked by displaying the name of the next module or course and by explicitly signaling when the learner is about to exit the player. 

### What's new

**"Next Module: {ModuleName}" label in the player**

The Next icon in the Fluidic Player now shows the name of the next module in the course. For example, Next Module: Lesson 2- Getting started. 

This applies wherever the learner is moving from one module to the next within the same course. 

**Clear exit action on the last module** 

When the learner is on the last module in a course, a new Exit action button appears, indicating that clicking it will close the player and return them to the course context. 

**Responsive behavior for mobile and PDF content** 

On smaller viewports (for example, ~320 px width), the Next label may be shortened or hidden, showing only the icon, to avoid overlapping with PDF controls. 

For PDF modules, the player adjusts controls to a separate line, so navigation labels and PDF controls don't interfere with each other. 

**Updated Admin > Branding > Player preview** 

The player preview in Admin > Branding now reflects the new label, for example, Next Module: Lesson 2. This allows administrators to see the updated navigation behavior. 

### Key benefits

**Clearer navigation for learners** 

Learners no longer have to guess what will happen when they select "Next." The label clearly specifies what comes next, whether it's a module or a course. This reduction in ambiguity helps alleviate hesitation and confusion, particularly in large customer education audiences where many learners may not be familiar with LMS interfaces. 

**Higher course‑completion rates** 

Clearly stating the next step (Next Module: {ModuleName}) and adding a distinct Exit action for the final module reduces the likelihood of learners abandoning the course or overlooking the last completion step. 

**More predictable user experience across devices** 

The updated labels align with the Next or Previous behavior and icons across desktop, tablet, and mobile. Layout constraints are respected across devices and PDF flows so that controls remain usable and accessible.  

This is particularly important for headless implementations where the Fluidic Player is embedded inside a custom learning experience. 

### Use cases

**Customer and partner education portals (headless or AEM‑integrated)**

Accounts utilizing Adobe Learning Manager in a fully headless setup, directing learners from external marketing channels. These learners: 

* Often consume video content in long sequences. 

* Expect a curriculum‑style experience where the system clearly indicates the next episode/module. 

In these environments, the **Next Module: {ModuleName}** label: 

* Reinforces the guided nature of the journey. 

* Minimizes drop‑off between modules. 

**Compliance and certification courses with ordered modules** 

In regulated or compliance‑heavy scenarios: 

* Learners must complete a strict sequence of modules. 

* Authors often disable TOC to avoid skipping. 

Here, showing **Next Module: {ModuleName}**: 

* Confirms to learners that they are following the correct sequence. 

* Makes it less likely that they misinterpret the Next action and exit early. 

**Learning Paths where courses follow each other** 

Where Learning Paths or equivalents chain multiple courses. This is useful when building curriculum‑style sequences for large audiences. 

**Mobile‑first consumption** 

For learners primarily using phones or tablets: 

* Updated labels and responsive behavior ensure navigation remains understandable without relying on tiny close icons or hidden controls. 

* This is important for customer education, gig workers, or frontline learners who may access content in short sessions on mobile devices. 

## Zoom Connector - create multiple concurrent Zoom sessions

### Overview

The Zoom Connector upgrade enhances how Adobe Learning Manager manages Virtual Instructor-Led Training (VILT). Before, users could only create one Zoom session at a time. With the new update, administrators and authors can schedule multiple Zoom sessions at the same time using standard integration.

### What's new

#### Support for multiple concurrent Zoom sessions via the connector

* The Zoom Connector now allows more than one VILT session at the same date/time to be created from ALM. 

* The scheduling logic no longer enforces a "one Zoom meeting at a time" constraint at the account/connector level. 

* Administrators and authors can configure overlapping VILT sessions (for example, regional classrooms, parallel tracks, or repeated sessions for different partner groups) without workarounds.

#### Meetings are created using the instructor's Zoom identity (not the Zoom super admin) 

To safely support concurrent meetings, the connector has been updated so that: 

* Zoom meetings are now created using the instructor's email address, instead of the Zoom super admin email. 

* Each instructor's Zoom account can host its own meetings in parallel with other instructors, subject to the limits of the existing Zoom plan.

**Note**: 

* Only one instructor per meeting is still supported. 

* If an instructor's email is later updated in Adobe Learning Manager, existing meetings remain associated with the original email used at creation.

#### No more manual Zoom URL pasting for concurrent sessions 

Previously, when a second or third Zoom session had to run at the same time: 

* Authors had to manually create Zoom meetings outside ALM and then paste the Zoom join URL into the course instance configuration. 

* This was error‑prone and did not benefit from connector features like attendance tracking. 

With the updated connector: 

* All sessions can be created directly from the ALM UI using the Zoom Connector, even if they overlap in time. 

* Session lifecycle (creation/cancellation) continues to be managed centrally via integration.

### Key benefits

#### Better VILT scheduling at scale 

Organizations can now: 

* Run multiple Zoom‑based virtual classrooms at the same time (for example, parallel tracks at a virtual summit, regional cohorts, or separate partner training sessions). 

* Avoid bottlenecks that previously forced admins to serialize sessions or rely on manual Zoom management. 

#### Reduced administrator and author overhead 

The enhancement eliminates: 

* Manual creation of Zoom meetings outside of Adobe Learning Manager. 

* Copy‑paste of Zoom URLs into each course instance for overlapping sessions. 

* Risk of mis‑configured links, wrong meetings being attached, or missed attendance tracking. 

Administrators and authors can manage all Zoom sessions from Adobe Learning Manager, using familiar workflows. 

#### Better alignment with Zoom provisioning and instructor roles 

By tying meetings to individual instructor Zoom accounts: 

* Each instructor can operate within their own Zoom license limits. 

* Organizations can use their existing Zoom provisioning model (one account per trainer, per BU, etc.) while still integrating fully with Adobe Learning Manager. 

* It avoids the single‑point bottleneck of using a shared super‑admin Zoom user for all sessions.

### Use cases

#### Multi‑track virtual events and summits 

Customer education teams running large events (for example, product bootcamps, partner summits, or certification weeks) can: 

* Configure multiple Zoom‑based sessions in the same time slot (for different tracks or topics). 

* Manage all of them as VILT modules under Adobe Learning Manager's courses and Learning Paths. 

* Provide learners a unified experience while the connector handles all underlying Zoom meeting creation.

#### Global partner and customer training 

Organizations that train customers and partners across regions can: 

* Run separate Zoom sessions for EMEA, APAC, and Americas at overlapping times to match local working hours. 

* Avoid forcing a single global time slot or manual Zoom setup for additional cohorts. 

#### Internal enablement 

Internal enablement teams (sales, support, and so on) can: 

* Schedule parallel onboarding sessions or role‑based breakouts (for example, separate Zoom rooms for developers, admins, and business stakeholders) in ALM. 

* Keep all sessions within ALM's VILT model for reporting and compliance purposes, rather than partially transitioning to unmanaged Zoom meetings.

## Show original author for shared courses in peer accounts 

### Overview 

When a course is shared through the catalog to a peer account, Adobe Learning Manager currently labels the author as "External Author" in the Learner, Administrator, and Author views of the receiving account. This can create challenges for learners and administrators, particularly in large enterprises, as it becomes difficult to identify and contact the appropriate content owner when issues or questions arise. 

The enhancement ensures that author information is preserved and surfaced for shared courses in peer accounts, rather than being replaced by a generic placeholder.   

### What's new 

Show actual author name for shared courses in peer accounts 

For courses shared via external or peer catalogs, the original author name from the source account is now displayed in the receiving account instead of "External Author". 

This applies to: 

* Learner app (course card or course details). 

* Administrator and author views when previewing as a learner. 

### Key benefits 

#### Direct owner visibility for shared content 

Learners and administrators in peer accounts can now: 

* See who authored the course, even when it is acquired via a shared catalog. 

* Avoid the generic and unhelpful "External Author" label. 

#### More consistent multi‑tenant and peer‑account experience 

For customers running multi‑tenant or extended‑enterprise scenarios: 

* The same course appears with consistent author branding across accounts. 

* The learner experience is aligned with expectations from the primary account (for example, seeing the source account's author name instead of "External Author"). 

### Use cases 

#### Large enterprise with peer accounts 

The enterprise uses ALM with: 

* A main account that owns the canonical courses, and 

* Peer accounts that acquire content via shared catalogs. 

Learners in peer accounts need to know which enterprise team authored a course to route questions or improvement suggestions correctly. 

With this enhancement: 

* Shared courses now display the correct enterprise author's name in peer accounts. 

* The enterprise's internal support load is reduced because learners and local admins know who to contact. 

#### Internal multi‑BU sharing 

Where one business unit curates learning for others: 

* The owning BU can be identified in the author field across all consuming accounts. 

* Local L&D admins can quickly see whether a course is maintained locally or by another BU, and collaborate accordingly.

## Expose Learning Object expiry (auto‑retire) date in Learner APIs 

### Overview 

This enhancement makes the auto‑retire date of a Learning Object (LO) available directly through Adobe Learning Manager's Learner‑facing APIs. When a course, learning path, or certification is configured with an expiry or auto‑retire date, that information is now part of the LO data returned by key Learner endpoints. 

### What's new 

#### New expiry/auto‑retire field in Learner LO APIs 

* The Learner LO APIs (for example, the endpoints that return learning objects to the learner experience and to external platforms) now include the LO expiry date (the auto‑retire date configured for that learning object). 

* This field is returned as part of the LO entity in responses such as: 

   * Get Learning Object (LO details). 

   * LO data used to populate learner home, catalog, and search results. 

* The field complements the existing completionDeadline that already exists at the instance level; the new field is specifically the LO‑level auto‑retire date. 

#### Availability in search‑backed learner experiences 

Because the expiry date is exposed as part of the search‑backed LO representation, it is now available anywhere ALM or an external platform uses: 

* search APIs or 

* search‑driven catalogs and suggestions to construct learner views. 

**Scope and exclusions** 

The enhancement applies to Learner APIs only. 

### Key benefits 

#### Expiry‑aware learner experience in custom LXPs 

For large and medium enterprises, their custom LXP can now obtain LO expiry information directly from ALM, allowing them to: 

* Show "Expiring on {date}" or "Expiring soon" labels on course cards and detail pages. 

* Communicate with urgency more clearly, so learners prioritize training that is about to retire. 

This is particularly important for compliance or time‑bound product training, where learning objects are regularly refreshed, and older versions are retired. 

#### Better guidance for learners on which trainings to take now 

By exposing LO expiry, the learner experience can: 

* Highlight courses that are still valid vs. ones about to be retired. 

* Help learners avoid enrolling in trainings that will no longer be available or valid in the near future. 

#### Consistency with existing completion deadline data 

Previously, learner APIs already exposed instance‑level completionDeadline, but not the LO‑level auto‑retire date. With this change: 

The following aspects of a training are available: 

* "By when must I finish this instance?" (completion deadline). 

* "Until when is this training offered?" (auto‑retire/expiry date). 

### Use cases 

#### A global enterprise with strict course lifecycle management 

Enterprises that regularly retire and replace courses (for example, regulatory, product, or methodology updates) can: 

* Avoid learner confusion about whether a training is being phased out. 

* Drive learners toward the most current, long‑lived offerings. 

Their custom portals and internal tools can now read the expiry date directly from ALM via the Learner APIs. 

#### External customer or partner academies 

For customer and partner education, marketing pages and portals often emphasize up‑to‑date training. 

Having expiry dates in the LO API lets experience builders: 

* Hide or de‑emphasize content that is close to retirement.

* Build "Last chance to complete" campaigns.

## Set restriction on module start time 

### Overview 

The enhancement lets authors and administrators in Adobe Learning Manager define a time window during which learners are allowed to start a module. Outside the configured start/end window, the module remains visible in the course structure, but learners cannot initiate it. 

This capability is critical for users who need tighter control over when certain content becomes available or should stop being initiated, for example, in timed programs, cohort‑based training, or time‑sensitive exercises. 

### What's new 

Authors can now configure, at the module level within a course, a start date/time and end date/time that governs when learners are allowed to launch that module. Within this window, the module behaves as usual; before the start time or after the end time, the learner sees the module in the course outline but cannot start it. 

The configuration appears in the course authoring user interface as additional scheduling controls for specific module types, such as self-paced content, quizzes, or activities. Administrators can use these controls to create modules that open in phases or to prevent late starts in programs where content must be consumed within a defined timeframe. 

#### Key benefits 

The main advantage is the ability to control when modules are accessible. Training teams can synchronize module availability with real-world events, such as new product launches, regulatory deadlines, and internal programs. This ensures that learners complete prerequisite content before they can access later modules. 

For instance, cohort 1 can access module 2 only in week 2, while module 3 will remain locked until week 3, eliminating the need to manually hide and unhide content or create separate course versions. 

This enhances the learner experience: instead of facing modules that can technically be accessed but shouldn't be at that time (or should already be completed), learners see a course structure where the modules they are permitted to start are clearly aligned with the intended schedule. 

#### Use cases 

* **Cohort-based enablement program**: In this program, each week opens a new module. The content for Week 1 is available immediately, while Week 2 is visible but cannot be started until a specified date. Week 3 follows the same gating process. Learners can see the entire learning path, but the system controls when they can actually begin each step. 

* **Time‑bound product or campaign training**: Marketing or product teams may create a training module that should only be accessed while a campaign is active or when a specific version of a product is still available. This designated start window ensures that learners don't begin a module about a discontinued product version after the specified end time. 

* **Assessment or exam environments**: Organizations can open a module (such as a test) for a short, well‑defined window (for example, "you may start the exam anytime between 9:00 and 12:00 on a given date"). Learners cannot begin the exam outside that window, which supports fair scheduling across time zones and cohorts.

## Control player language via custom LTI parameter 

### Overview 

The enhancement allows external platforms using LTI (Learning Tools Interoperability) to specify the language for Adobe Learning Manager content at the time of launch. Instead of depending on the learner to change the language within the Fluidic Player, the LTI consumer can send a language code through a custom LTI parameter. Adobe Learning Manager will then use this code to select the appropriate language variant. 

### What's new 

External platforms that act as LTI consumers can now pass a custom language parameter (and related player settings) when launching ALM content. ALM reads this parameter and: 

* Sets the player language accordingly. 

* Launches the corresponding language variant of the module, when multi‑language content is configured. 

This means a first‑time learner, who selects French on the external platform, will see the ALM player and module launch directly in French, without having to adjust anything inside ALM. 

The enhancement also accommodates scenarios in which the external platform treats ALM as a headless content player. For example, it allows the hiding of navigation elements and the table of contents (TOC) by sending additional custom parameters to adjust certain user interface settings. These settings work in conjunction with the language parameter, enabling the external platform to provide a smooth, branded experience while still utilizing ALM for playback and tracking. 

### Key benefits 

* **Consistent language experience across systems**: When a learner selects a language in the external portal, that choice is immediately reflected in ALM. This ensures that learners don't face any mismatch between the language of the portal and the course. As a result, they won't have to search for a language switch within the player. 

* **Language‑specific reporting**: In their platform, language selection is consistent with ALM, which enhances the accuracy of their analytics and learner tracking. This alignment also supports configurations where ALM's own language controls are intentionally disabled or hidden in the Fluidic Player for specific courses. In these cases, the external platform serves as the single source of truth for language. 

### Use cases 

* A significant use case involves large enterprises utilizing LTI-based integrations. Learners first enroll and select a language on the platform. They then launch ALM training sessions through LTI. With this enhancement, when a learner selects Spanish, the ALM module automatically opens in Spanish. This means that learners don't need to adjust the language settings in ALM. Furthermore, language-based reporting remains consistent with what learners see and experience in ALM. 

* Another application is the delivery of headless course experiences within a customer or partner portal. In this setup, the portal may embed ALM content using an iframe, while all navigation and language user experience (UX) are managed outside of ALM. By utilizing custom LTI parameters, the portal can ensure the ALM player is displayed in the correct language and that any unnecessary user interface elements (such as the table of contents and navigation buttons) are hidden. This allows learners to perceive a single, cohesive application rather than a disjointed collection of tools. 

* This is beneficial for organizations that conduct large-scale training in multiple languages using another LMS or learning platform. They can standardize their use of that platform for managing learner profiles, selecting locales, and presenting catalogs. Meanwhile, ALM serves as a reliable content and tracking engine, respecting the language preferences and user interactions specified by the external system during each LTI launch.

## Checklist question weightage for instructor evaluations 

### Overview 

The enhancement introduces weighted checklists, allowing instructors and managers to evaluate learners using graded scales and total scores, rather than treating each checklist question as equal. The goal is to facilitate checklist creation by implementing weighted evaluations of questions, which allows the reflection of the relative importance of different actions or skills within a single checklist. 

### What's new 

Checklists will support the following types: 

1. Yes/No 
Behavior remains the same as today: each question is Yes/No and pass criteria are based on the number of "Yes" responses. 

2. Same‑weight questions 

   * Questions are scored on a numeric scale (0–10 by default), where: 

      * The max/min values on the scale are customizable at the checklist level. 

      * The scale can now start at 0 (the previous minimum score was 1). 

   * All questions share the same maximum score, so the checklist behaves as a uniform graded scale for each question. 

3. Different‑weight questions 

   * Each question has its own maximum score (weight). 

   * The passing criteria depend on the percentage of the total possible score that the learner achieves across the checklist (for example, "pass if the learner achieves ≥ 70% of the total available score"). 

For all checklist types: 

* The **Reviewer** (instructor or manager) evaluates the learner according to the configured checklist type: 

   * Selecting Yes/No. 

   * Select scores on the defined scale. 

* The **Checklist** report is updated to include, for questions with different weightage: 

   * The maximum score for each question. 

   * The score achieved by each learner for that question. 

This allows analysis of overall performance and question-specific performance based on the intended weights. 

### Key benefits 

* **Richer, more realistic assessments**: Instructors can reflect real‑world priorities by giving more points to critical behaviors and fewer to minor ones, while still using a checklist workflow suited to observed or practical tasks. 

* **Total‑score‑based pass/fail**: Evaluations can be based on the overall percentage score, not just how many questions pass a threshold, aligning more closely with typical competency or grading schemes. 

* **Better reporting**: Updated checklist reports expose max score and achieved score per question, allowing program owners and quality teams to identify specific weak spots and refine training or evaluation guidance. 

### Use cases 

* **Enterprise skill assessments**: Engineers are assessed via practical, scenario‑based checklists where certain diagnostic or communication steps must carry more weight than cosmetic or low‑risk steps. Weighted questions and total‑score pass criteria make these assessments more credible and predictive of real‑world performance. 

* **Safety and compliance observations**: In healthcare, manufacturing, or field service, critical safety steps can be given higher max scores, ensuring that missing a safety‑critical action has a larger impact on the total score than missing a minor procedural step. 

* **Coaching and calibration**: With max and achieved scores per question in the report, managers can see exactly where learners underperform and calibrate instructors on how to score consistently.

## Checklist with commenting capability for reviewer 

### Overview 

The enhancement introduces a commenting feature for checklist evaluations, allowing reviewers, such as instructors and managers, to provide qualitative feedback alongside the numeric scores. This feedback can be made visible to learners when necessary.  

The goal is to support checklist-based evaluations where mentor feedback is as crucial as the numeric result. This includes highlighting specific strengths, areas for improvement, or providing context for the given score. 

Today, reviewers can: 

* Evaluate a checklist for each learner, question by question. 

* View results and re‑evaluate learners who have failed. 

In real-world scenarios, such as aviation, field trainers assess shop-floor agents and airport staff. Similarly, instructors and mentors in small and medium-sized enterprises (SMEs) often use checklists to evaluate job performance. However, these checklists typically do not include a structured section for capturing narrative feedback related to the evaluation. 

### What's new 

#### Authoring options 

Authors can configure each checklist to: 

* Enable or disable commenting capability for reviewers. 

* Decide whether the reviewer's name should be shown to learners along with comments. 

This allows organizations to tailor comment visibility to their culture and privacy requirements. 

#### Reviewer experience 

When commenting is enabled: 

* Reviewers (instructors/managers) can add optional comments while evaluating a checklist. 

* They can choose whether comments are visible to learners, based on the checklist settings. 

If they re‑evaluate a learner, they can update or change comments to reflect the latest assessment. 

#### Reporting and notifications 

* The Checklist report gains a new column for reviewer's remarks, capturing the comment provided during evaluation. 

* Learners receive notifications (in‑platform and email) whenever a checklist evaluation occurs. These notifications include: 

   * The comment and 

   * The reviewer's name, if those were configured to be visible. 

This ensures feedback is not only stored but actively surfaced to learners. 

### Key benefits 

* **Richer, coach‑like feedback**: Numeric scores are supplemented with contextual remarks, making checklists a more effective tool for coaching, not just compliance. 

* **Traceability and auditability**: Organizations gain a persistent record of who evaluated whom, when, and what they said, which is important in regulated environments and high‑stakes roles. 

* **Better learner engagement**: Learners receive clear guidance linked to specific evaluations, which improves their understanding of expectations and subsequent steps. 

### Use cases 

* Organizations with regulated environments can use comments to document clinical judgment or procedural feedback for staff who are being observed in the field. 

* Aviation and ground‑handling organizations can attach detailed notes on operational performance, safety practices, and customer‑facing behavior, turning a checklist into a structured debrief tool. 

* In mentoring and SME evaluation, instructors can capture nuanced observations that wouldn't fit into a score alone, for example, "handled escalation well but needs to improve time management" or "excellent troubleshooting flow; missed a documentation step."

## Content‑level multiple attempts and quiz reporting 

### Overview 

>[!IMPORTANT]
>
>Note that the feature will only be available after enabling it in the account. Contact ALM support.


Presently, ALM supports multiple attempts at the LMS level via the Multiple Quiz Attempt (MQA) feature: 

* Authors can configure attempts at course level (applied to all quiz‑bearing modules in the course) or at module level (per quiz module). 

* Attempts can be: 

   * A specific number (for example, 3 attempts), or 

   * Infinite attempts, controlled at LMS level. 

* When a learner consumes a module through the Fluidic Player and then closes the player or completes the module, that session is treated as a single LMS attempt. 

* Each LMS attempt is captured in the L2 quiz report as a new row. 

However, if the content file itself (for example, an Articulate SCORM quiz) implements its own multiple‑attempt logic, ALM's L2 quiz report does not currently distinguish or track those internal attempts correctly. 

This enhancement introduces content-level multiple attempt tracking for quizzes, allowing Adobe Learning Manager to accurately capture each attempt within the content itself in the L2 quiz report. It's designed for situations where the content authoring tool (such as Articulate SCORM) manages quiz attempts independently. With this feature, attempts are correctly reflected in ALM reporting without depending on LMS-level Multiple Quiz Attempt (MQA) settings. 

### What's new 

#### Author flag for content‑level attempts 

* When uploading content into the Content Library, authors can now indicate that a specific content file has multiple attempts embedded within it. 

* This is a per‑content setting that tells ALM to treat attempts defined inside the content as the source of truth. 

#### Course/module behavior 

When such content is used in a course: 

* The module will derive its attempts from the content, not from LMS MQA. 

* Learners will see one LMS‑level attempt only: 

   * The course overview and module view does not expose an LMS "re‑attempt" button for that module. 

   * Attempt handling (for example, re‑tries within the quiz) is governed by the content itself. 

#### Reporting 

The L2 quiz report treats each content‑level attempt as a separate attempt row: 

* Each internal quiz attempt configured in the content appears as its own row in the L2 quiz report, like how LMS‑level attempts are represented today. 

* The format of each row remains the same as existing multi‑attempt rows in L2 reporting (same columns, structure, and semantics). 

* This gives a consistent reporting experience: 

   * Whether attempts are controlled by LMS MQA or by the content, the L2 quiz report shows one row per attempt. 

#### Key benefits 

* Accurate attempt history for SCORM quizzes where attempts are controlled internally by tools like Articulate, without forcing LMS‑level MQA configuration on top. 

* Cleaner learner experience: for content‑controlled attempts, learners see a single slot at the LMS level and don't need to interact with LMS re‑attempt controls; all re‑tries are handled within the quiz UI they already know. 

* Flexible architecture: Users can choose whether ALM MQA or content‑level attempts should drive behavior per module, depending on how their content was authored and how they prefer to manage attempts. 

* Consistent reporting model: downstream consumers of the L2 quiz report can treat each row as "one attempt," regardless of where the attempt logic originates. 

#### Use cases 

* Organizations using Articulate SCORM can keep self-contained quiz logic within the SCORM package while achieving accurate attempt-level reporting in ALM without extra LMS configuration. 

* Organizations that use vendor-supplied SCORM content can avoid the need to modify or implement additional attempt and retry logic with LMS-level MQA.

## Instructor QR codes for instance enrollment and session attendance 

### Overview 

This enhancement adds the ability for instructors to generate QR codes themselves for: 

* Course instance enrollment, 

* Session attendance, or 

* Enrollment + attendance together 

at the session level. It's designed for situations where learners enter a physical or hybrid classroom and require a quick, self-service option to enroll and record their attendance using a QR code. 

### What's new 

#### Instructor‑generated QR codes 

* Instructors can generate QR codes at the session level for: 

   * Enroll in instance: Learners scan to enroll into the instance that includes the current session. 

   * Mark session attendance: Learners scan during/after the session to record attendance for that specific session. 

   * Enroll in instance + mark session attendance : A combined QR for walk‑ins who are not yet enrolled and need their attendance marked in one step. 

* Instructors can export the QR codes they need based on the scenario (enrollment, attendance, or both). 

#### QR code packaging 

The exported QR code PDF includes: 

* Course name 

* Instance name 

* Session name

These make it easy for instructors and coordinators to identify and print the correct QR code for each session. 

### Key benefits 

* **Instructor autonomy**: Instructors no longer need to wait for admins to create QR codes. They can generate them directly for each session, improving agility and reducing coordination overhead. 

* **Better classroom logistics**: For walk‑in or on‑site audiences (such as field workers, shop‑floor staff, or external attendees), instructors can manage enrollment and attendance on the spot using QR codes. 

* **Reduced admin workload**: Admin teams can focus on configuration and governance instead of handling routine QR code generation requests for every session. 

### Use cases 

* Organizations running large volumes of on‑site sessions (for example, product training for professionals) can enable instructors to print session‑specific QR codes that enroll and mark attendance with one scan. 

* In retail, manufacturing, and healthcare training, where learners often join sessions directly from the floor or without pre-enrollment, an "Enroll + Attendance" QR code can be placed at the door. This allows learners to self-serve their enrollment and attendance via their phones. 

* Training events for partners or customers allow the on-site trainer to easily adapt to changes in the room, additional sessions, or extra attendees without needing to consult the administrator for new QR codes.

## Captivate and ALM player improvements 

### Overview 

This enhancement improves the experience of playing Adobe Captivate content within the Adobe Learning Manager (ALM) player, particularly following the recent changes to Captivate's architecture. The aim is to allow learners to engage with Captivate modules natively in ALM while ensuring that navigation, completion tracking, and note-taking are clear, consistent, and reliable. 

### What's new 

#### Unified TOC experience 

* Only the ALM TOC is displayed on the left side of the player. 

* Captivate's own TOC is hidden when the module is played within ALM. 

* This removes duplication, ensures a single source of truth for navigation, and frees up screen real estate. 

#### Visual completion feedback 

* The ALM TOC shows green tick marks (or equivalent visual cues) indicating slide‑level completion. 

* As learners progress through Captivate slides, the ALM TOC reflects which slides have been completed, aligning with learner expectations for modern course players. 

#### Contextual progress controls 

* The player controls will adapt based on slide type: 

   * For video slides: 

      * Show a time progress bar, reflecting video playback. 

* For non‑video slides: 

   * Display slide navigation controls (next/previous slide, etc.) instead of a non‑functional time bar. 

      * This avoids showing irrelevant or non‑working controls on certain slide types. 

#### Streamlined navigation 

* The separate module navigation bar (ALM) and course navigation bar is merged into a single, intuitive bar. 

* This unified navigation: 

   * Clearly distinguishes moving through the Captivate module vs. moving back to course/module level. 

   * Reduces confusion caused by multiple bars with overlapping purposes. 

#### Reliable notes linking 

* Notes are linked to slide numbers rather than timestamps. 

* This change: 

   * Fixes export failures caused by missing or incorrect timestamps. 

   * Ensures notes can be exported consistently as PDFs, with a reliable mapping between notes and the slide context they belong to. 

### Key benefits 

* Cleaner, single‑player experience: Learners interact with one TOC and one navigation model, reducing confusion and cognitive load. 

* Accurate completion and progress indications: Slide‑level ticks and contextual controls help learners understand where they are and what's left. 

* More reliable note‑taking and exports: By tying notes to slides instead of fragile timestamps, users regain a reliable notes‑to‑PDF workflow, even with slide‑based Captivate content. 

* Preserved author workflow: Authors retain the simplicity of Captivate's direct publish to ALM, while learners get a modern, integrated playback experience without extra authoring burdens. 

### Use cases 

* Enablement programs that rely on Captivate for interactive simulations can deploy content into ALM, ensuring that navigation, completion tracking, and notes function consistently for learners. 

* Organizations using Captivate as their main content authoring tool can maintain one-click publishing and avoid confusing double TOCs and non-functional controls for learners. 

* Organizations that rely on notes exported from Captivate content in ALM (for coaching, compliance, or records) can access the following: 

   * Notes link correctly to slides. 

   * PDFs are generated as expected.

## Improved learning time spent calculation in Learner Transcripts

### Overview

Adobe Learning Manager has revised how it calculates learning time in Learner Transcripts with its April 2026 release. Previously, the reporting logic could lead to inaccurate times if learners left the player open without engaging with the content, causing discrepancies. The new method now tracks active time based on user engagement, specifically when the tab is in focus and when there is user activity. This change results in more accurate data.

This update improves reports and dashboards, helping administrators better ensure compliance and track learner progress. After the release, review your Learner Transcripts to see these enhancements.

The updated calculation method focuses on actual engagement, such as active tab focus and recent user interactions, thereby improving the accuracy of time reporting across the following areas:

* Learner Transcripts (UI)
* Admin Dashboard metrics
* Course Enrollment reports
* APIs and Connectors

### What's changed

The **Learning Time Spent** column in Learner Transcripts now uses improved logic to calculate time more accurately. Instead of simply tracking player open/close times, the system now distinguishes between active and idle periods based on user engagement.

* **Active time**: Time when the learner is actively engaged (for example, on the correct tab, performing actions like scrolling or watching video).
* **Idle time**: Time when the learner is not engaged (for example, tab switched, no activity for 10+ minutes), which is excluded from the total.

This applies to most module types, with exceptions for SCORM, Captivate, and XAPI modules, which retain the original logic.

### How it works

The new calculation varies by module type:

* **Video and audio modules**: Active when the content is playing, even if the learner switches to another tab. Tab focus is not required for tracking playback time.
* **Static modules (PDF, PPT, Excel, and so on)**: Active if on the tab and performing activities (mouse movement, scrolling, clicking, keyboard input) within the last 10 minutes. If there is no activity for 10 minutes, it switches to idle.
* **SCORM and Captivate** retain the original open/close logic.
* **xAPI** now uses tab‑based active time detection, where time is counted only when the tab is active. Note that AICC content **is not** supported.
* **HTML, LTI, and Other Content**: May vary; check Learner Transcripts for accuracy.

Idle time is subtracted, ensuring only true engagement time is reported.

>[!NOTE]
>
>If your laptop goes into sleep mode, learning time may not be tracked correctly. This is because activity tracking pauses while the system is asleep and resumes only when the laptop wakes up.


### Summary table

| **Module type** | **Active time (counted)** | **Idle time (excluded)** |
| --- | --- | --- |
| **Video / Audio** | Playback time | Not started; ended; paused **\>10 min** |
| **Static (PDF/PPT/DOC)** | Tab active **and** activity in last **10 min** | No activity **\>10 min**; tab inactive |
| **SCORM** | Time reported by content runtime | Idle cannot be detected |
| **Captivate** | Slide‑based timing | Idle cannot be detected |
| **xAPI** | Tab active | Tab inactive |
| **HTML** | Player open time with tab active | Tab inactive |
| **LTI Producer/Consumer** | If LTI content is played within ALM's player (that is, ALM is consuming LTI content hosted on another LMS acting as the Producer), then this time‑spent logic applies.<br><br>However, if the content is played outside the LMS (that is, the content is hosted in ALM, then ALM is the Producer, but the playback happens in an external player), this portion of the time‑calculation logic does not apply.  <br>**Note**: LTI Consumer is not supported in Adobe Learning Manager. | Tab inactive |

**Note**:

* **Revisits and parallel sessions**: Count as active when the above conditions are met.
* **All devices, browsers, languages**: Included; offline mobile usage is added after sync.

### Benefits of the new calculation

* **Accurate reporting**: Eliminates inflated times from unattended players, providing realistic learning durations.
* **Better compliance**: Supports accurate tracking for mandatory training (for example, a company's 5-hour monthly requirement).
* **Improved dashboards**: User activity graphs and time-spent reports now reflect actual engagement.
* **Learner insights**: Helps administrators identify genuine progress and address disengaged learners.

### Reporting and analytics impact

* **Learner Transcripts:** "Learning Time Spent" now reflects **actual engagement**.
* **Admin Dashboard:** Metrics that include time (for example, "time spent" tiles, trends) will show **lower but more realistic** values in scenarios where idle time previously inflated results.
* **Course Enrollment reports:** Time‑related fields adopt the **new calculation** post‑launch.
* **Comparability note:** Because historical data is not recalculated, time‑series analyses that span the release date may show a **step change**. Consider annotation or segmentation by date in analytics tools.

### API and connectors

* **No schema changes** to existing endpoints/fields that report time spent.
* **Field semantics** are updated to reflect _active‑time calculation_ for sessions **after** the feature launch.
* **Connectors and exports** consuming time‑spent fields will automatically receive the updated values going forward.

### Backward compatibility and data migration

* **Historical sessions:** Not recalculated.
* **New sessions:** Use the **new** active‑time calculation.
* **Mixed periods:** For audits or longitudinal reporting, segment by **pre‑/post‑launch** to avoid misinterpretation.

### Known limitations

* **Interactive content** (SCORM/Captivate) continues to rely on content‑provided timing; idle detection within the content is not available.
* **Iframe‑based content** (HTML/xAPI) limits detection of fine‑grained interactions; tab focus is used instead.

### Frequently asked questions

**Does this update change historical records?**

No. The change applies only to sessions after the feature launch.

**How do I verify the changes?**

Check Learner Transcripts for recent modules; compare times to expected durations.

**Does this affect all accounts?**

Yes, it's a global update for all Adobe Learning Manager accounts.

**Do learners need to take action?**

No. The change is automatic and transparent to learners.

**What if learners leave content open?**

Idle time is now excluded, preventing over-reporting.

**Are video/audio sessions auto‑paused when the tab is inactive?**

No. Playback behavior is unchanged. Time is excluded when paused >10 minutes or when not actively playing.

**Will offline mobile activity be reflected?**

Yes. Offline usage is included when the device syncs.

**What should I do if my dashboards now show lower averages?**

This is expected where idle time had previously inflated results. Annotate dashboards and adjust targets as needed.

**Are there any prerequisites?**

None; the change is automatic.

## Update to Learning Transcript reports for Administrators

We are updating the Learning Transcript (LT) reports for Admins to better support checklist-based evaluations and reviewer feedback.

## What is changing?

### 1. Column Rename in Admin Learning Transcript

The existing **Submission comment** column in the Admin Learning
Transcript is:

1. **Renamed to:** `Reviewer's remarks`

### Data shown in this column:

* **For submission modules:**
   The column continues to display the submission comment (no behavioral change).

* **For checklist modules:**
   The column now displays the evaluation comment (the checklist reviewer's remarks).

This change applies to all Admin LT sources:

* LT downloaded from the Admin UI
* LT obtained via the Job API
* LT generated via Connectors

After this change, the same column carries: - Submission comments for submission modules

* Evaluation comments for checklist modules

Under the new header name **Reviewer's remarks**.

### 2. New Column in Connector-Based Learning Transcript Exports

For connector-exported Learning Transcripts:

* A new column named **Reviewer's remarks** is added at the end of the report.
* This column contains the reviewer's comments, aligned with the behavior described above:
    * Submission comments for submission modules
    * Evaluation comments for checklist modules

## Impact on existing integrations and automations

If you are using Learning Transcript reports in custom integrations, automations, or external reporting tools, please review the following scenarios:

| Scenario | Impact | Action required |
|----------|--------|----------------|
| You identify fields in Admin LT by column name (for example, "Submission comment") | The column header changes to Reviewer's remarks. | Yes. Update any mappings or logic that reference Submission comment to use Reviewer's remarks. |
| You identify fields in Admin LT by column position only (index-based) | The position of this column remains the same in Admin LT. | Usually no action. If your logic does not depend on the header text, no change is needed for Admin LT, just change the column name if currently 'Submission Comments' column is used. |
| You use connector-exported LT and rely on a fixed column count or specific last-column position | A new column is appended at the end of the report. | Yes. Adjust parsing or validation logic to account for an extra column at the end of the file. |
| You use connector-exported LT and map by column name | A new column Reviewer's remarks is available. | Optional. No change is required unless you want to consume the new reviewer/checklist comments data. |

**What you should do**

* Review any scripts, ETL jobs, dashboards, or integrations that consume Admin Learning Transcript reports.
* If you reference the old column name _Submission comment_, update your configuration or code to use the new column name Reviewer's remarks.
* If you use connector-based LT exports and assume a fixed number of columns or a fixed last column, update your logic to handle an additional column at the end of the export.

If your current implementation relies purely on column positions in Admin LT and does not validate or depend on the column header text, no change is required for the Admin LT itself. Only connector exports need attention when you depend on a fixed layout.


## Non-logged-in experience in Experience Builder

The non-logged-in experience in Experience Builder allows organizations to display their learning content and portal pages to all visitors, including those who have not signed in. This feature is designed to attract, inform, and engage prospective learners by offering a smooth and branded preview of your training offerings before requiring them to log in or enroll.

This feature lets you create and customize public-facing pages using the same user-friendly drag-and-drop interface found in the standard Experience Builder. You can showcase course catalogs, categories, paths, and rich static content, including images, text, HTML, and embedded iframes, for anyone visiting your portal. This makes it simple to highlight your learning programs, promote new courses, and provide essential information to a broader audience.

Visitors can browse the catalog, view details about courses and instances, and utilize the global search to explore available training opportunities. However, actions that require a user's identity, such as enrolling in a course, accessing personalized features (like, Calendar, Compliance, Leaderboard, or Social Learning), or consuming training, will prompt the visitor to log in. This approach ensures that sensitive and personalized information remains secure while still allowing for a comprehensive preview experience.

Administrators have the ability to configure which pages and widgets are visible to users who are not logged in, ensuring that only suitable content is displayed. Pages can be set to be accessible to both logged-in and non-logged-in users, or exclusively for one of these groups. The Experience Builder offers a preview mode, allowing you to see exactly how your pages will appear to visitors before they are published.

To enable this feature, your ALM integration administrator must activate the Training Data Access Connector. This connector ensures that course metadata is publicly accessible.

Branding and localization are fully supported, enabling you to customize page titles, favicons, and language settings to align with your organization's identity and meet your audience's needs. As part of the transition to this enhanced experience, the legacy homepage feature for non-logged-in users will be deprecated. Therefore, all new public content should be created using Experience Builder.

### Purpose of the feature

The non-logged-in experience in Experience Builder allows organizations to publicly showcase their learning content and portal pages to anyone, without requiring users to log in. This helps attract, inform, and engage potential learners by providing a preview of available training and resources before enrollment or authentication is needed.

### Real-world use cases on non-logged-in experience

* **Marketing and outreach**: Organizations can promote their training programs to external audiences, such as prospective customers, partners, or job applicants, by making course catalogs and program details publicly accessible.
* **Pre-enrollment exploration**: Learners can browse available courses, view overviews, and explore categories before deciding to sign up or log in, helping them make informed enrollment decisions.
* **Corporate training portals**: Companies can provide a public-facing portal for compliance or onboarding information, allowing new hires or contractors to see what training is available before they receive credentials.
* **Event or campaign landing pages**: Organizations running learning campaigns or events can create dedicated public pages to highlight featured courses, schedules, or resources, increasing visibility and engagement.
* **SEO and discoverability**: By making select pages and catalogs public, organizations improve their search engine visibility, helping people to discover their learning offerings online.

### Key concepts of non-logged in experience

Experience Builder's non-logged-in experience lets you publicly showcase learning content and portal pages, allowing visitors to browse without logging in.

* **Create public pages and menus**: You set up pages and a single menu that everyone can access, regardless of login status.
* **Add only supported widgets**: You include widgets that don't need user context (categories, courses and learning paths, content box, HTML, iframe), while the system hides user-specific widgets.
* **Configure adaptive page behavior**: You decide if a page appears for both logged in and non logged in users, and the system adapts visible widgets and content based on login state.
* **Preview both experiences**: You use preview options to see how pages look for logged in and non logged in users, with differences in widget visibility and content.
* **Enable global search**: Visitors search for courses and content, but only get basic search features without advanced AI integration.
* **Let visitors browse catalog and course overviews**: Visitors explore catalog pages, course details, and instances, but must log in to enroll or access personalized features.
* **Customize branding and localization**: You set favicons, and language settings to match your organization's branding and accessibility needs.
* **Enable the Training Data Access Connector**: You activate this connector to export course metadata for public display, keeping non-logged-in pages up to date.
* **Handle high traffic with shared infrastructure**: The system manages large volumes of anonymous visitors using shared resources and rate limiting.
* **Optimize for SEO**: The platform prepares public pages for search engine indexing, making your learning content simpler to find.

### Prerequisites for non-logged in experience

* You must enable the Training Data Access Connector in the integration admin before you can use the non logged in experience.
* The connector exports course metadata to a public repository, which keeps non logged in pages updated.

#### Training Data Access connector initialization

The Training Data Access (TDA) connector is a critical prerequisite for enabling the new non-logged-in experience builder feature in ALM. This connector facilitates the export of training metadata, allowing your portal to display course information to users who are not logged in.

* **Connector activation**: You must enable the TDA connector from the integration admin panel. This step enables the non-logged-in experience builder functionality and makes relevant UI options visible in your admin interface.
* **Metadata export**: Once activated, the connector exports essential training metadata (such as course name, description, overview, rating, duration, and skills) from ALM to a public repository. This data is used to populate non-logged-in pages and widgets.
* **Scheduling and synchronization**: The export process can be scheduled (for example, daily) to ensure your portal reflects the latest course updates. Changes made in ALM will appear on your non-logged-in pages after the next export cycle, subject to caching and export frequency.
* **Feature availability**: The non-logged-in experience builder features, including menu creation, widget support, and catalog visibility, are only accessible after the TDA connector is initialized. If the connector is not enabled, your experience builder will remain limited to logged-in user scenarios.
* **Migration and support**: For accounts transitioning from legacy non-logged-in homepage features, initializing the TDA connector is the first step toward migration. It ensures you can use the new experience builder's flexibility and enhanced capabilities.


### What visitors can do without logging in

On a non-logged-in Experience Builder site, visitors can browse the training catalog by opening the catalog page for public catalogs. They can use filters such as catalog, product, role, type, skills, and tags, depending on how you have configured the site. Visitors can also search for trainings using the global search bar in the header (if enabled), and view search results directly on the catalog page.

Visitors can view training details by opening overview pages for courses, learning paths, and certifications. These pages display key metadata, including the title, description, author, duration, format, tags, and skills.

In addition, visitors can explore static and promotional content. They can read text and rich content blocks, view banners and image tiles, and interact with embedded iframes such as external microsites, videos, or tools.

If a visitor clicks enroll or tries to start training, the system prompts them to log in or sign up. After successful login, the visitor is redirected to the appropriate page, whether it is the home page, a custom page, or the specific training they selected.

### What's not available without logging in

On a non-logged-in Experience Builder site, visitors cannot access features or content that require user authentication. They are unable to enroll in trainings, start or consume courses, or access personalized widgets such as My Learning, Calendar, Compliance, Leaderboard, or Social Learning. These widgets depend on user-specific data and are only available after logging in.

Visitors also cannot perform actions like enrolling in a course or accessing any content that requires tracking progress or user context. Attempting to enroll or start a training prompts the visitor to log in or sign up before proceeding.

### Supported widgets in non-logged-in mode

In non-logged-in mode, only widgets that do not require user-specific data are supported. These include:

* Categories widget, which displays available training categories.
* Courses and paths widget, which shows courses and learning paths from the public catalog.
* Content box, for adding static text, images, or promotional content.
* HTML widget, for embedding custom HTML content.
* Iframe widget, for displaying external sites, videos, or tools within the page.
* Widgets that require user context, such as My Learning, Calendar, Compliance, Leaderboard, and Social Learning, are not available in non-logged-in mode.

### Pages and menus in non-logged-in experience

* Only one non-logged-in menu is supported, visible to all visitors without authentication.
* Pages can be added to both logged-in and non-logged-in menus; if a page is in both, it adapts its widgets and content based on the user's login state.
* Non-logged-in menus do not have audience targeting or personalization. Everyone sees the same set of pages.
* Widgets not supported in non-logged-in mode are hidden automatically; page layout adjusts to fill gaps.
* Menu and page management (adding, previewing, deleting) is like logged-in mode, but with adaptations for non-logged-in constraints.

### Search and catalog behavior

In non-logged-in mode, users can access the catalog page and use search to browse available courses and learning paths. The catalog page displays all public courses, along with filters and search functionality, following the same account settings as in logged-in mode. When a user searches, the results appear on the catalog page, and users can view course and instance overview pages without logging in. However, actions like enrollment require login.

If a user attempts to enroll, the system requires them to log in first. The search for non-logged-in users is simpler than that for logged-in users and does not include advanced features like AI Assistant integration.

### Technical implementation

#### Training data access connector setup

You must enable the training data access connector in the integration admin panel before you can use the non-logged-in experience builder feature. This connector exports training metadata from ALM to a public repository, making it accessible via APIs for your non-logged-in pages. The connector setup is a prerequisite for activating the feature and ensures your portal displays up-to-date training information.

#### Metadata export and synchronization

The connector exports key metadata fields such as course name, overview, description, rating, duration, and skills. You can schedule exports (for example, daily) to keep your portal synchronized with ALM. Not all metadata fields may be included; consult engineering for a complete list. Exported data is used to populate non-logged-in pages, and changes in ALM will appear after the next export cycle.

#### Caching and export frequency

The system uses backend export frequency and frontend caching to manage data updates. Changes made in ALM are reflected on your portal after the scheduled export and cache refresh. Some updates may not appear immediately due to these mechanisms. If you need faster updates, adjust the export schedule or clear the cache as needed.

#### CSS/JS customization support

You can apply custom CSS and JavaScript to both logged-in and non-logged-in pages using the customization tab. This allows you to maintain consistent branding, add custom UI elements, and enhance user experience across your portal. All customizations are applied globally, ensuring a unified look and feel.

#### URL differences and branding (favicon, page title)

Non-logged-in and logged-in pages may have different URLs to distinguish user states. You can customize the favicon and page title for your portal, helping reinforce your brand identity. These features are available in the experience builder; check with engineering for the latest status on non-logged-in support.

### Performance and scalability

#### Shared stack vs premium stack

The shared stack allows multiple customers to use the non-logged-in experience builder on common infrastructure, supporting standard traffic levels. The premium stack is a paid option that provides dedicated resources, real-time features, and higher seat limits for customers with advanced needs. Select the stack based on your expected traffic and business requirements.

#### Traffic limits and rate limiting

The shared stack enforces traffic limits to ensure fair usage among customers. Engineering will implement rate limiting to prevent any single customer from consuming all resources. If you plan marketing campaigns or expect high traffic, coordinate with engineering to understand your limits and avoid service disruptions. Rate limiting helps maintain system stability and performance for all users.

#### Multi-tenancy and SEO considerations

The platform supports multi-tenancy, allowing multiple customers to host their portals on shared infrastructure. Non-logged-in pages are SEO-friendly, along with sitemap.xml and robots.txt to optimize search engine visibility. This ensures your portal is discoverable and indexed appropriately by search engines.

### Migration and deprecation

#### Transition from existing non-logged-in homepage

You should recreate your homepage using the new experience builder for enhanced flexibility, widget support, and improved user experience. The transition plan ensures minimal disruption and continued support.

#### Communication plan

Customers using the legacy homepage will receive clear communication about the deprecation timeline and migration steps. Support will be provided to help you move your homepage to the new experience builder platform, ensuring you benefit from new features and ongoing updates.

### Localization and login support

#### Locale fallback logic

The system displays pages in the locale they were created. If a user's locale is unavailable, the system uses a fallback logic to select the next best available locale. This ensures users always see content in a supported language, improving accessibility and user satisfaction.

#### Supported login types

The non-logged-in experience supports all login types available in ALM, including SSO and standard login. Users can browse content without logging in and will be prompted to log in when required, such as enrolling in a course or accessing personalized features. This provides a smooth transition from browsing to engagement.


### Non-logged in APIs

#### Admin Learning Object API

Non-logged-in Experience Builder pages and headless portals often organize or filter courses based on product and role. The Admin LO API has been enhanced to ensure that these associations are consistently accessible for back-end and headless integrations, as well as for the TDA connector.

**Endpoint and behavior**

You continue to use the existing Admin LO endpoint:

```
GET /primeapi/v2/learningObjects/{loId}?enforcedFields[learningObject]=products,roles
```

Where:

* loId is the learning object ID (for example course:12345).
* enforcedFields[learningObject] instructs the API to explicitly include products and roles for that LO.

This is fulfilled by ensuring that the LO's product and role associations are present in the response when requested through enforcedFields. The response then contains, in attributes, the product and role metadata needed to compute or expose the recommended products (rec\_products) and roles (rec\_roles) for Experience Builder and other consumers.

A typical call from an admin or integration looks like:

```
url -X GET \
 "https://{your-domain}/primeapi/v2/learningObjects/course:12345?enforcedFields[learningObject]=products,roles" \
 -H "Authorization: Bearer {admin\_token}" \
 -H "Accept: application/vnd.api+json
```

The returned LO JSON is the same basic structure as before, but now you can rely on product/role fields being present when you request them with enforcedFields. Integrations that do not use enforcedFields continue to behave as before.

#### Learning Objects Listing – JobAid Support in effectiveModifiedDate Filter

**Purpose**

The Training Data Access (TDA) connector and headless implementations often need to perform incremental synchronization, based on the **effective modification date** of learning objects. Until this release, JobAids (LO type jobAid) were not correctly handled when combined with the effectiveModifiedDate filters. This release fixes this so JobAids can be synced incrementally like courses and learning paths.

**Endpoint and behavior**

You use the existing LO listing endpoint with date filters and LO type:

```
GET /primeapi/v2/learningObjects
 ?filter.effectiveModifiedDate.fromDate=2025-03-15T13:14:56.000Z
 &filter.effectiveModifiedDate.toDate=2025-03-20T13:14:56.000Z
 &filter.loTypes=jobAid
```

Previously, when filter.loTypes=jobAid was combined with an effectiveModifiedDate range, the filter effectively excluded JobAids, and the call behaved as though JobAids were not supported.

From this update onwards, the call returns only JobAid learning objects whose effectiveModifiedDate falls inside the specified window.

```
{
 "links": {
 "self": "https://acapapiserver/primeapi/v2/learningObjects?page[limit]=10&filter.effectiveModifiedDate.fromDate=2026-01-19T13:14:56.000Z&filter.effectiveModifiedDate.toDate=2026-01-21T13:14:56.000Z&filter.loTypes=jobAid"
 },
 "data": [
 {
 "id": "jobAid:144968",
 "type": "learningObject",
 "attributes": {
 "authorNames": ["Author"],
 "dateCreated": "2026-01-20T08:48:55.000Z",
 "datePublished": "2026-01-20T08:48:55.000Z",
 "dateUpdated": "2026-01-20T08:48:55.000Z",
 "effectiveModifiedDate": "2026-01-05T07:31:18.000Z",
 "loType": "jobAid",
 "loFormat": "Content",
 "loResourceType": "Content",
 "localizedMetadata": [
 {
 "description": "Link jobAid new",
 "locale": "en-US",
 "name": "Link jobAid new"
 },
 {
 "description": "Link jobAid new fre",
 "locale": "fr-FR",
 "name": "Link jobAid new fre"
 }
 ],
 "relationships": {
 "authors": {
 "data": [
 { "id": "13385176", "type": "user" }
 ]
 },
 "instances": {
 "data": [
 { "id": "jobAid:144891\_-1", "type": "learningObjectInstance" }
 ]
 }
 }
 }
 }
 ]
}
```

This means you can now safely implement incremental JobAid syncs based on effectiveModifiedDate, in the same way you already do for other types.

If you omit filter.loTypes=jobAid, the behavior for other LO types is unchanged; the change only affects the combination of JobAid with that filter.

#### **Menu API: Non-logged-in menu filter**

**Purpose**

Experience Builder and headless frontends need a straightforward way to retrieve the **non-logged-in menu** , the one that defines navigation for public visitors. Before this release, you had to fetch all menus and then apply custom logic to identify which one represented the non-logged-in navigation. This release adds a simple server-side filter.

**Endpoint and behavior**

You use the existing Menu listing endpoint with a new query parameter:

```
GET /primeapi/v2/templates/menus?include=pages,subMenus.pages&isNonLoggedIn=true
```

The key points:

* include=pages,subMenus.pages is optional but recommended when you need the page and submenu page details in the same response.
* isNonLoggedIn=true is new in this release and tells the server to return only menus that are flagged as non-logged-in menus.

Without the isNonLoggedIn parameter, the endpoint behaves exactly as before and returns menus according to the existing default behavior. With isNonLoggedIn=true, it typically returns the single menu used by the non-logged-in experience for your account (since there is normally one non-logged-in menu per account).

In practice, a client can now issue:

```
curl -X GET \
 "https://{your-domain}/primeapi/v2/templates/menus?include=pages,subMenus.pages&isNonLoggedIn=true" \
 -H "Authorization: Bearer {admin\_token}" \
 -H "Accept: application/vnd.api+json"
```

and get back the non-logged-in navigation structure in one call, with all the pages that should be visible to anonymous visitors.

This is particularly useful when you are building a headless non-logged-in site and want to mirror the same navigation that Experience Builder uses, or when you are debugging whether the non-logged-in menu has been configured correctly.

### Allow listing of custom domains

The non-logged-in stack consists of:

* A public CDN domain (for example cpcontents.adobe.com or yourdomain.example.com) that serves layouts, config JSON, and static assets.
* A public Elasticsearch (ES) endpoint that serves catalog and search data, but only if the request comes from an **allow-listed domain** for that ALM account.

When you introduce a custom domain, it works seamlessly without any additional effort following the existing process for adding a custom domain.

#### Prerequisites

Before whitelisting a custom domain for non-logged-in:

1. The custom domain is configured for your ALM account (for example, DNS for academy.yourcompany.com points to Adobe / Akamai, and certificates are provisioned).
2. The **Training Data Access (TDA) connector** is enabled for the account.
3. The **non-logged-in Experience Builder** feature is enabled (Adobe-side).

These steps ensure that:

* Your account has a non-logged-in **account JSON** (often referenced as accountConfig / experienceBuilderConfig), which includes fields such as cpDomain, almDomain, almCdnBaseUrl, esBaseUrl, and allow-listed domains.
* The non-logged-in stack knows where to serve data and from which domains it should accept requests.

#### How allow-listing works

The allow-list is stored in the configuration that TDA exports and the non-logged-in stack reads. That configuration includes:

* The ALM domains (cpDomain, almDomain).
* The **CDN base URL** for non-logged-in content (almCdnBaseUrl).
* The **public search base URL** (esBaseUrl).
* The list of domains that are allowed to make public non-logged-in calls for that account.

For non-logged-in Experience Builder to work on a custom domain:

* The browser must load the non-logged-in HTML from that custom domain (or from the ALM non-logged-in CDN domain, depending on your setup).
* Calls from that domain to the public ES and CDN endpoints must be accepted. That only happens if the domain is present in the allow-list.

This release adds a new non-logged-in CDN domain, cpcontents.adobe.com, and specifies that it must be placed into the **allow-listed domains** in the TDA connector. For existing non-logged-in native users, this requires an update.

#### Allow-list a custom domain

**Configure the custom domain in ALM**

Work with Adobe to register your domain, for example, academy.yourcompany.com, as the custom domain for your ALM account. You update DNS to point to Adobe Akamai as instructed and wait for SSL and routing to complete.

At this point, both logged-in and non-logged-in traffic can reach ALM through that domain, but non-logged-in search and catalog calls may still be blocked if the domain is not allow-listed.

**Enable TDA and non-logged-in Experience Builder**

Ensure that:

* The **Training Data Access connector** is enabled.
* The **non-logged-in Experience Builder** feature is turned on for the account.

Enabling TDA creates or updates the non-logged-in account JSON. For new accounts, the process also allow-lists the new non-logged-in CDN domain (cpcontent.adobe.com) by default, so the public ES endpoint expects calls from that domain.

For accounts that were already using the older non-logged-in stack, existing connectors must be deleted and recreated to pick up the new domain.

**Add the custom domain to the allow-list**

The critical part is telling the non-logged-in ES stack that academy.yourcompany.com is an approved origin. There are two common paths.

1. **Re-enable the TDA connector (simple, self-service friendly)**

Existing native non-logged-in users will need to delete and re-enable the TDA connection so the new domain is automatically allow-listed. Doing this achieves two things:

1. The non-logged-in account JSON is regenerated.
2. The allow-listed domains are updated to include the new non-logged-in CDN domain and your custom domain.

This is recommended when you have a small number of accounts and can tolerate temporarily disabling and re-enabling the connector.

1. **Verify that the domain is actually allow-listed**

After allow-listing, open your non-logged-in site on the custom domain and inspect the browser network calls.

You want to see:

* Requests to almCdnBaseUrl (for example <https://cpcontent.adobe.com/>...) succeeding with 200/304.
* Requests to esBaseUrl (public search API, for example <https://primeapps.adobe.com/almsearch/api/v1/>...) succeeding, returning JSON with search / catalog data.

If these calls return 4xx or explicit errors suggesting "untrusted domain" or "origin not allowed," the allow-list is incomplete or misconfigured and Support needs to adjust it.

The non-logged-in LLD also notes that the account config can hold an expected domain value. At runtime, the site checks that the domain in the URL matches what is set in the config; if it does not, the user can be redirected to an error page. This protects against one customer's configuration being accessed via another customer's domain.

### Using recommendations in the non-logged-in Experience Builder

The non-logged-in Experience Builder lets you build public learning pages where visitors can browse your catalog and see highlighted content before they sign in. Even though these visitors are anonymous, you can still present recommended trainings by using metadata and widgets.

In the logged-in learner app, recommendations can be personalized: they can depend on the learner's profile, history, skills, and progress. In the **non-logged-in** experience, there is no learner identity yet, so the platform cannot personalize per user.

Recommendations in non-logged-in mode are therefore:

* **Curated or rule-based**: based on catalog, product, role, labels, tags, and other metadata.
* **Segment-oriented**: "recommended for developers", "recommended for partners", "featured for beginners".
* **Marketing-focused**: used to attract and guide visitors to enroll once they log in.

### Metadata and APIs that support recommendations

Behind the scenes, non-logged-in pages use:

* The **TDA connector** to export learning object metadata (courses, paths, certifications, job aids) to a public search index.
* The **public search stack** to answer queries from non-logged-in widgets (catalog, search, Courses and paths, Categories).
* The **Admin Learning Objects API** to expose product and role metadata that can be used for recommendation rules.

In this release, the Admin LO API was extended so that product and role associations are reliably available:

```
GET /primeapi/v2/learningObjects/{loId}?enforcedFields[learningObject]=products,roles
```

This allows widgets and headless integrations to build rule-based recommendations using products, roles, catalog labels, tags and other fields consistently.

### Designing recommendation sections with Experience Builder widgets

You create recommendation sections on non-logged-in pages by combining **Experience Builder widgets** with metadata filters.

#### **Courses and Paths widget**

Use the **Courses and Paths** widget when you want to show a row or grid of recommended items. In its configuration you can choose:

* Which catalogs to pull from.
* Which catalog labels, products, roles or tags to use as filters.
* Whether to show courses, paths, certifications, job aids, or a mix.
* Sorting and maximum number of items.

For example, you can create:

* "Recommended for developers": filter by a product or role you use for developer content.
* "Start here": filter by a label such as "Starter" or "Onboarding".
* "Featured this quarter": filter by a time-bound label like featured-q3-2026.

The widget is not learning from behavior; it is showing whatever matches the metadata rules you define. From a visitor's point of view, however, it looks like a recommendation strip.

#### **Categories widget**

Use the **Categories** widget to help visitors navigate into "recommended" sets of content, even if they do not know your product names.

You can configure tiles that each represent a segment such as:

* "For administrators"
* "For sales teams"
* "For partners"
* "By product line"

Each tile can link either to:

* A filtered catalog page (for example, the catalog filtered by certain products or labels).
* A dedicated non-logged-in page that uses Courses and paths preconfigured for that segment.

This gives you a "recommended paths by segment" experience without personalization.

### Building segment-based recommendations

Because non-logged-in visitors have no ALM profile yet, it is useful to design recommendations **by segment** and let visitors self-select.

1. Use a **non-logged-in home page** that briefly explains who your academy is for and shows a small number of segment entry points (for example, "Developers", "Marketers", "Partners", "New employees"). This can be done with a Categories widget or a simple Content box or HTML section with buttons.
2. For each segment, create a **dedicated non-logged-in page** in Experience Builder. On that page use one or more Courses and paths widgets configured with filters that represent what is "recommended" for that group. For example, for "Developers" you might filter on:
   1. Catalog = "Public Training"
   2. Product = "Adobe Experience Manager"
   3. Tags = "Developer fundamentals"
3. Use those segment pages as the destination of your marketing campaigns and as the target of the tiles on the non-logged-in home page.

Visitors perceive that they are seeing recommendations tailored to their situation, even though the logic is defined at design time via metadata.

### Transitioning from non-logged-in to personalized recommendations

Non-logged-in recommendations are mainly about **discoverability** and **conversion**. Once visitors decide to enroll or start training, they will log in and become full learners with a profile and history.

The usual flow is:

1. A visitor discovers content through your non-logged-in recommendation sections (home recommendations, segment landing pages, featured rows).
2. They click into a course or path overview and choose to enroll or start.
3. ALM prompts them to sign up or log in.
4. After they log in, the standard logged-in learner experience takes over, including:
   1. "My Learning"
   2. Logged-in catalog with personal progress
   3. Any internal recommendation systems you use for existing learners.

In other words, the logged-in recommendations help them decide what to do next and keep going.

### How job aids can be used in the new non-logged-in Experience Builder

On the **User Interface**, job aids participate in non-logged-in experiences mainly through the widgets that can show learning objects:

1. **Courses and paths widget**
   This widget can show multiple LO types, including job aids. In non-logged-in pages you can configure it to:
   1. Include or exclude job aids explicitly.
   2. Filter job aids by catalog, product, role, labels, tags, and other metadata.
   3. Present them alongside courses and paths or as a separate "Resources" strip.

For example, on a public landing page you might configure one strip titled "Helpful resources" that shows job aids only, and another strip titled "Recommended courses" that shows courses and paths.

1. **Catalog page and search**
   The non-logged-in **catalog** and **search** surfaces use the public search index (fed by the Training Data Access connector). That index now supports job aids correctly, so:
   1. Non-logged-in search results can include job aids.
   2. Non-logged-in catalog filters (by type, product, tags, etc.) can include job aids as long as your account configuration and widgets are set up to show them.
2. **LO overview pages**
   When a visitor clicks a job aid from any widget or from the catalog, they go to an **LO overview page** for that job aid in non-logged-in mode. From there, they can read its description and metadata. Actual download or consumption typically still requires login, but the presence and discoverability of the job aid itself is handled by the non-logged-in experience.

### How job aids are exposed through non-logged-in APIs

On the **API side**, job aids are supported by:

1. The **Training Data Access connector and public search**
   TDA exports job aid metadata along with other LO types to the public search index that serves non-logged-in search and catalog queries. This is what Experience Builder and headless frontends rely on.
2. The **Learning Objects listing with effectiveModifiedDate**
   In this release, the LO listing endpoint was corrected so that job aids work properly with the effectiveModifiedDate filter. You can now call:

```
GET /primeapi/v2/learningObjects
 ?filter.effectiveModifiedDate.fromDate=2026-01-19T13:14:56.000Z
 &filter.effectiveModifiedDate.toDate=2026-01-21T13:14:56.000Z
 &filter.loTypes=jobAid
```

Before this change, combining effectiveModifiedDate with loTypes=jobAid did not reliably return job aids. That means:

1. Your TDA or ETL jobs can **incrementally sync job aids** for non-logged-in experiences, the same way they do for courses and paths.
2. Any headless implementation that builds a public job aid directory can query changes based on effectiveModifiedDate and loType=jobAid.

**Note**:

In the non-logged-in state:

* Job aids are mainly **discoverable**: visitors can see that they exist, read descriptions, and understand how they support topics or courses.
* Actual **consumption** (downloading or opening the job aid content) typically still requires login, especially if job aids are considered part of licensed or internal content.

### Changes in brief description in LO search (non-logged-in)

In the non-logged-in stack, search and listing of learning objects (LOs) are powered by the Training Data Access (TDA) connector and a public Elasticsearch index. Historically, this stack used a single overview/description field for each LO. Customers building headless non-logged-in portals wanted to show the same short description on LO tiles that the logged-in learner UI shows, rather than only the long overview.

The change introduces support for the LO **brief description** in non-logged-in search and listing APIs:

* For **courses**, the existing UI semantics are:
* Logged-in cards show Brief description (140-character field) if present; otherwise they fall back to the long Detailed overview.
* For **learning paths**, the logged-in UI uses the Benefits field as the short description, if defined, and falls back to the overview otherwise.
* For **certifications**, a short Description is used, with a longer Certification overview as fallback.
* For **job aids**, the main description field is used.

### Other changes

#### Restriction that no two accounts can share the same custom domain

In the non-logged-in and logged-in architectures of Adobe Learning Manager, a **custom domain** (for example, academy.example.com) is treated as a globally unique key that must map to exactly one ALM account, so the platform enforces a hard restriction that **no two accounts can share the same custom domain**. This is required for security, routing, and SEO: the routing layer and non-logged-in stack use the domain to look up the correct account configuration (including its non-logged-in account JSON, Experience Builder menus, branding, and TDA/search endpoints),

Allowing the same custom domain on two accounts would make it impossible to guarantee which account's data is returned, could cause cross-tenant leakage, and would also corrupt generated artifacts such as sitemap.xml and robots.txt that are produced per account but discovered by search engines per host. Operationally, this means that when you assign or move a custom domain you must first ensure it is not attached to any other account (or de-register it there), and Adobe's internal tooling will reject attempts to bind the same domain to multiple accounts.

#### Browser caching of resources in the non-logged-in experience

In the non-logged-in experience of Adobe Learning Manager, browser caching of resources is a core part of the performance and scale strategy, because public pages must handle large, sometimes spiky marketing traffic with low latency and minimal origin load. Static and semi-static assets such as the non-logged-in HTML shell (for example, index.html/guest.html), account-level configuration JSON (account.json or config.json), Experience Builder page layout JSON (menus, widget layouts, card settings), CSS, JS, images, and favicons are served from an Akamai CDN (cpcontents.adobe.com / cpcontent.adobe.com) with cache headers that encourage both CDN-side and browser-side reuse, so that after the first page load the browser can render subsequent non-logged-in pages largely from its cache, revalidating only when needed via ETag or Last-Modified.

## Multi-lingual Job Aids

### Introduction

Multilingual Job Aids in Adobe Learning Manager (ALM) let authors and administrators provide supporting documents, guides, or resources in multiple languages within a single job aid entry. Learners across different regions can access relevant materials in their preferred language, which improves comprehension, compliance, and user experience.

### Previous behavior

Previously, job aids in ALM supported only a single content file per job aid, even when the name and description could be localized. To provide the same resource in multiple languages, authors had to create separate job aids for each language. This led to duplication, confusion, and increased administrative overhead. There was no unified way to manage multilingual resources, which made it difficult to ensure consistency and track usage.

### Use cases

* **Global workforce enablement**: Deliver safety manuals, process guides, or reference documents in multiple languages to a diverse workforce.
* **Regulatory compliance**: Ensure all employees receive the same compliance documentation in their native language.
* **Consistent onboarding**: Provide onboarding checklists or FAQs in local languages for new hires worldwide.
* **Reduced duplication**: Manage all language versions of a job aid in a single entry, which simplifies updates and reporting.

### Key features

* **Multiple language support**: Attach a unique file or URL for each supported language within a single job aid.
* **Localized name and description**: Enter the job aid's name and description in each language.
* **Unified management**: Edit, update, and report on all language versions from one place.
* **Backward compatibility**: Existing single-language job aids are automatically replicated across all added languages until new files are uploaded.

### Create a multilingual job aid

1. Go to the Author role and select **Job Aids**.
2. Select **Create Job Aid**.
3. Enter the job aid's name and description in the default language.
4. Add the primary content file or URL for the default language.
5. Save the job aid.

### Add additional languages

1. In the job aid editor, select **Add Language**.
2. Select the desired language(s) from the list.
3. For each added language:
   * Enter the localized name and description.
   * Upload the corresponding content file or provide a language-specific URL.
4. Repeat for all required languages.

### Edit and manage languages

1. To update a file or description for a specific language, select the language tab and make changes as needed.
2. If a language is added after the job aid is published, the original file is automatically assigned to the new language until a unique file is uploaded.
3. Remove or replace files for any language as required.

### Publish and learner experience

1. After all languages and files are added, publish the job aid.
2. Learners see the job aid in their selected content language, with the appropriate file or URL.
3. If a learner's language is not available, the default language file is shown.

### Reporting

1. Download job aid reports to view details of all files and languages associated with each job aid.
2. Reports include language, file name, and usage data for tracking.

### Best practices

* Provide accurate translations for names, descriptions, and content files.
* Review and update files regularly to ensure consistency across languages.
* Use clear naming conventions to distinguish files for different languages.
* Test the learner experience by switching content languages to verify correct file delivery.

### Troubleshooting

* **Missing file for a language**: The default file is shown. Ensure all languages have the correct file uploaded.
* **Legacy job aids**: Add new language files to replace automatically replicated originals.
* **Wrong language shown**: Check the learner's content language settings and the job aid's language configuration.

Multilingual Job Aids let you deliver supporting resources to a global audience in a single entry, reduce duplication, and ensure every learner receives the right information in their preferred language. This feature improves accessibility, compliance, and administrative efficiency in Adobe Learning Manager.

## Get answers with AI Assistant for learners

AI Assistant for learners is a conversational, AI-driven assistant within Adobe Learning Manager designed to guide you to the information you need faster. By asking questions in natural language, you can get contextual explanations, surface relevant courses, and retrieve insights from learning content — without manually browsing through catalogs.

### Capabilities

* **Smart question-answering:** Handles both single-turn and multi-turn conversations, letting you ask questions naturally. Responses are derived from courses, learning paths, certifications, and job aids.
* **Content-grounded answers with citations:** Pulls information directly from learning materials and includes citations that point back to the original course, module, or resource.
* **Broad content compatibility:** Supports a wide range of formats, including documents, presentations, videos, audio files, HTML content, and Sharable Content Object Reference Model (SCORM) modules.
* **Seamless user experience:** Available as a side panel across learner pages, maintaining session-based chat history for continuity.
* **Robust administrator controls:** Administrators can enable or disable the assistant, limit access by user groups, and choose which internal catalogs are used as the source for AI-generated responses.

### Benefits

* **Faster access to knowledge:** You receive instant answers to your questions, eliminating the need to navigate through multiple courses or documents.
* **Higher engagement:** Conversational interactions make the learning experience more natural, intuitive, and accessible.
* **Better understanding:** You can ask follow-up questions to clarify concepts and explore topics more thoroughly.
* **Scalable learning support:** Automated, AI-driven responses minimize dependence on subject-matter experts and support teams.

Learn more about [AI Assistant for learners](/help/migrated/learners/feature-summary/learner-ai-assistant.md).

## Multi-lingual Video Text Tracks (VTT) support

Multi-lingual Video Text Tracks (VTT) support in Adobe Learning Manager enables authors to provide subtitles and captions for video and audio content in multiple languages. This feature streamlines localization, making training accessible to a global audience and ensuring compliance with accessibility standards. Authors can auto-generate, translate, review, and edit VTT files directly within the platform.

### Use Cases

* **Global Training:** Deliver video content with subtitles in multiple languages to reach international learners.  
* **Accessibility Compliance:** Provide captions for hearing-impaired users in their preferred language.  
* **Faster Localization:** Reduce manual effort and accelerate content rollout by auto-generating and translating VTT files.  
* **Consistent Experience:** Ensure all learners receive the same information, regardless of language.

### Key features

* **Automatic VTT generation:** Upload a video or audio file and auto-generate VTT captions in the original language.  
* **Multi-language translation:** Translate captions into any of the 39 supported non-English languages.  
* **In-app review and editing:** Review, edit, and download VTT files before publishing.  
* **Notifications:** Receive in-app notifications when VTT generation and translation are complete.  
* **Smooth publishing:** Publish finalized captions for learners to access in their chosen language.

### Upload content and generate VTT

1. Go to the Content Library and select **Add Content**.
2. Upload your MP3 or MP4 file.
3. In the upload dialog, select the option to **Generate Translation**.
4. Select the original content language (default is the file's language).
5. Select additional target languages for translation (up to 39 supported).
6. Select **Save**. The system begins generating and translating VTT files.

### Monitor progress

1. After saving, the new content entry appears in the Content Library.
2. A progress indicator shows the status of VTT generation and translation.
3. You receive an in-app notification when the process is complete.

### Review and edit VTT files

1. In the Content Library, open the content in **Edit** mode.
2. For each language, select the **Review** link next to the VTT file.
3. A pop-up displays the captions for that language.
4. Edit captions directly in the pop-up or download the VTT file for offline editing.
5. After making changes, upload or paste the revised captions back into the pop-up.
6. Save your edits.

### Publish captions

1. When satisfied with all language captions, publish the content.
2. Learners see subtitle options in all published languages when viewing the video.

### Additional Information

* **Supported Languages:** All 39 non-English languages supported by Adobe Learning Manager.  
* **Notifications:** Authors are notified when VTT generation and translation are complete.  
* **Editing flexibility:** Captions can be edited in-app or offline and re-uploaded.  
* **Scalability:** Designed for enterprise-scale localization and accessibility needs.  
* **No Need for Manual VTT Upload:** The system can generate VTT files from scratch using the uploaded video/audio.  

### Best Practices

* Always review auto-generated captions for accuracy before publishing.  
* Provide translations for all major learner groups to maximize accessibility.  
* Use the notification system to stay updated on processing status.  
* Regularly update captions if video content changes.  

### Troubleshooting

* If VTT generation fails, ensure your file is in a supported format (MP3/MP4).  
* For missing languages, verify they are supported and selected during upload.  
* If captions are out of sync, use the in-app editor to adjust timing.  

Multi-lingual VTT support enables you to deliver accessible, localized video learning experiences efficiently. By using auto-generation, translation, and in-app editing, you can ensure your content reaches and supports all learners, regardless of language.

## Design custom certificates

Custom Certificates in Adobe Learning Manager (ALM) let administrators and authors design, manage, and issue personalized certificates for learners. The feature includes a drag-and-drop editor, dynamic fields, multilingual support, and AI-generated backgrounds so organizations can create branded certificates without technical expertise.

### Previous behavior

Previously, certificate creation in ALM was limited by template rigidity, lack of customization, and technical barriers (such as HTML editing). Customers requested simpler ways to design certificates, add dynamic fields (such as learner name or instructor), and support multiple languages, all while maintaining brand consistency and visual appeal.

### Use cases

* **Branded recognition**: Issue certificates with corporate logos, colors, and fonts for compliance, training, or achievement.
* **Dynamic personalization**: Automatically populate learner names, instructor names, and other active fields.
* **Multilingual delivery**: Provide certificates in multiple languages for global learners.
* **Flexible design**: Create landscape or portrait certificates, use AI-generated backgrounds, and preview before publishing.

### Access custom certificates

1. Go to the **Achievements** section in the Admin home page (previously called **Badges**).
2. Select **Certificates** to view, create, or manage certificate templates.

### Create a certificate

1. Select **Create Certificate**.
2. Select portrait or landscape orientation.
3. Select an existing template or start from a blank canvas.
4. Enter a certificate name and default language.
5. Use the drag-and-drop editor to add:
   * Text fields (with font, color, and positioning options)
   * Images (logos, icons, etc.)
   * Dynamic fields (learner name, instructor name, etc.)
   * Certificate backgrounds (solid color, uploaded image, or AI-generated image)
6. For AI-generated backgrounds: Enter a prompt (for example, "students in a classroom") to generate backgrounds using AI.

### Add dynamic fields

Dynamic fields in Adobe Learning Manager custom certificates are placeholders that automatically populate with relevant information, such as learner name, instructor name, or other account-specific data—when the certificate is generated, allowing for personalized and context-aware certificates without manual editing.

1. Insert dynamic variables such as learner name, instructor name, or other active fields.
2. Fields are automatically populated when the certificate is issued.

### Multilingual support

1. Add new languages (for example, French, German) to the certificate.
2. Enter translated text for each language.
3. Manage translations and preview certificates in each language.

### Preview and publish

1. Use the preview feature to see how the certificate appears to learners.
2. Download or print the preview for review.
3. Save as draft to continue editing later, or publish when ready.

### Apply certificates

1. Admins can set default certificates for the account.
2. Authors can attach certificates to specific learning object instances (courses, paths, etc.).
3. Select different certificates at the instance level as needed.

### Manage certificates

1. View published and draft certificates in the library.
2. Edit, update, or delete templates as required.
3. Certificates can be reused across multiple instances.

Custom Certificates in ALM provide a flexible way to design and issue personalized, branded, and multilingual certificates. The feature simplifies certificate management, improves learner recognition, and supports global compliance and branding needs.

## Multi-lingual Job Aids

Multilingual Job Aids in Adobe Learning Manager (ALM) let authors and administrators provide supporting documents, guides, or resources in multiple languages within a single job aid entry. Learners across different regions can access relevant materials in their preferred language, which improves accessibility, compliance, and user experience.

### Previous behavior

Previously, ALM allowed only one content file per job aid, even though the name and description could be localized. To provide the same resource in multiple languages, authors had to create separate job aids for each language. This led to duplication, confusion, and increased administrative effort. There was no unified way to manage multilingual resources, which made it difficult to ensure consistency and track usage.

### Use cases

* **Global workforce enablement**: Deliver safety manuals, process guides, or reference documents in multiple languages to a diverse workforce.
* **Regulatory compliance**: Ensure all employees receive the same compliance documentation in their native language.
* **Consistent onboarding**: Provide onboarding checklists or FAQs in local languages for new hires worldwide.
* **Reduced duplication**: Manage all language versions of a job aid in a single entry, which simplifies updates and reporting.

### Create a multilingual Job Aid

1. Go to the Author role and select **Job Aids**.
2. Select **Create Job Aid**.
3. Enter the job aid's name and description in the default language.
4. Upload the primary content file or provide a URL for the default language.
5. Save the job aid.

### Add additional languages

1. In the job aid editor, select **Add Language**.
2. Select the desired language(s) from the list.
3. For each added language:
   * Enter the localized name and description.
   * Upload the corresponding content file or provide a language-specific URL.
4. Repeat for all required languages.

### Edit and manage languages

1. To update a file or description for a specific language, select the language tab and make changes as needed.
2. If a language is added after the job aid is published, the original file is automatically assigned to the new language until a unique file is uploaded.
3. Remove or replace files for any language as required.

### Publish and learner experience

1. After all languages and files are added, publish the job aid.
2. Learners see the job aid in their selected content language, with the appropriate file or URL.
3. If a learner's language is not available, the default language file is shown.

### Reporting

1. Download job aid reports to view details of all files and languages associated with each job aid.
2. Reports include language, file name, and usage data for tracking.

Multilingual Job Aids in ALM let you deliver supporting resources to a global audience in a single entry, reduce duplication, and ensure every learner receives the right information in their preferred language. This feature improves accessibility, compliance, and administrative efficiency in Adobe Learning Manager.

## Playback improvements for Captivate generated courses

The update significantly improves the playback experience for Adobe Captivate content within ALM by introducing a unified and streamlined interface.

The ALM player now displays a single, consolidated TOC, hiding the Captivate TOC, and provides clear slide-level completion indicators, including green tick marks for visual progress tracking.

The system simplifies navigation by merging module and course controls into one intuitive bar, reducing learner confusion.

Context-aware progress controls enhance usability by displaying video progress bars only on video slides and slide navigation controls only on non-video slides.

Additionally, the system now links notes to slide numbers instead of timestamps, ensuring reliable PDF exports and resolving prior format inconsistencies.

## Checklist enhancements

### Multi-language support for checklist

This feature lets you create and manage checklist modules in multiple languages. Each checklist question, instruction, and evaluation criterion can be translated so reviewers and learners interact with the checklist in their preferred language. The system displays the checklist in the user's selected content language, which improves accessibility and compliance for global teams.

1. Add or edit a checklist module in your course.
2. Select all the languages you want to support from the language options.
3. For each language, enter translations for every checklist question, instruction, and evaluation criterion.
4. Save your changes. The checklist displays in the reviewer's or learner's selected content language.
5. If you add a new language later, provide translations for all questions and criteria before publishing.
6. When downloading checklist reports, select your preferred language to view the report in that language.

### Checklist question weightage for instructor evaluations

This feature lets you assign different maximum scores (weightage) to each checklist question. You can reflect the varying importance or difficulty of each question, which supports more accurate and meaningful evaluations. The system calculates the total score based on your input and determines if the learner passes or fails according to the criteria you set.

1. When adding a checklist module, select **Custom scoring**.
2. For each checklist question, set a unique maximum score that reflects its importance.
3. Define the overall passing score for the checklist.
4. Save and publish the checklist.
5. As an instructor or reviewer, evaluate each learner by assigning a score for every question (up to the maximum you set).
6. The system calculates the total score and determines pass/fail status.
7. Download checklist reports to view both achieved and maximum scores for each question and the total score.

### Checklist with commenting capability for reviewer

This feature lets reviewers add comments or feedback during checklist evaluation. You can provide personalized, actionable feedback for each learner. You can also choose to display your name with your comments for transparency. All remarks are saved in the learner's transcript and included in checklist reports.

1. When setting up the checklist, enable **Reviewer remarks**.
2. Optionally, enable **Show reviewer name to learner** if you want your name to appear with your comments.
3. During evaluation, enter comments or feedback for the learner in the provided remarks field.
4. Select whether your comments should be visible to the learner.
5. Submit your evaluation. If enabled, the learner sees your remarks and your name alongside their results.
6. All comments are saved in the learner's transcript and included in checklist reports for future reference.

## Advanced search enhancements

This release includes improvement in in-content search by showing the courses with content match with query higher in rank. Also, Job Aids are now included in advanced search ranking.

## Equivalents and alternates

### Overview

In many organizations, learners encounter training situations where different courses can legitimately satisfy the same requirement?for example, when a new course replaces an older one, when a more comprehensive course can stand in for a shorter one, or when a special substitute course needs to be offered.

The Alternate Courses or Learning Path feature gives ALM a formal way to say:

"If the learner completed this training, treat them as having satisfied that related training requirement."

The feature works across courses and Learning Paths, ensures downstream requirements such as prerequisites and compliance rules are honored, and does this without forcing learners to sit through redundant content. It also keeps reporting accurate by recording what was completed directly versus what was satisfied via an alternate.

At the core, the feature introduces the concept of an alternate completion: a special completion state created automatically when a learner finishes a configured source training that counts towards another target training.

### Equivalence vs. alternates

Some training relationships are bidirectional, meaning each course can satisfy the other's requirement. This is effectively a scenario where two trainings are treated as mutually substitutable. In contrast, unidirectional relationships allow one training to satisfy the requirement for another, but not vice versa. ALM models both scenarios using the same underlying alternate*completion mechanism.

* **Bidirectional relationship:** Completing either training satisfies the requirement for the other.
* **Unidirectional relationship:** Completing Training A satisfies Training B, but completing B does not satisfy A. This is common when a newer or more comprehensive version should count toward an older requirement, but not the reverse.

Alternates are most often used in **unidirectional** scenarios?for example, when a more comprehensive superset course covers everything in a simpler subset course. Completing the superset should satisfy the requirement for the subset, but not necessarily the other way around.

* A newer, expanded course that should count toward an older requirement.
* A course designed for a specific audience (for example, a regional or accessibility*adapted variant) that still fulfills the same requirement as the primary course.
* An enhanced new version of a course that the organization wants to count for an older requirement, but the older version should not count for the new requirement.

In Alternates, the relationship is normally **one*way**. If Course A is an alternate for Course B, completing A can satisfy B's requirement, but completing B does not necessarily satisfy A.

Both equivalence and alternate share the same underlying mechanism in ALM: when a configured source training is completed, ALM automatically produces an alternate completion for one or more target trainings.

### What problems does this solve?

Without Alternates and Equivalence, administrators and learners face several recurring issues:

* Learners are frequently asked to repeat courses that cover content they already completed in a different version or format.
* Updating compliance programs is simpler because admins can replace or restructure trainings without forcing learners who completed older versions to retake equivalent or superseded content.
* Prerequisite logic is rigid. If a path requires a particular course as a prerequisite, there is no clean way to recognize that another training is good enough.
* Reporting and audits are harder. There is no formal signal showing that a requirement was satisfied via an alternate completion and no straightforward way to trace the source of the credit.

The Alternates and Equivalence feature addresses these issues by:

* Preventing duplicate effort for learners when alternates are valid.
* Allowing admins to modify training structures (for example, swap a course inside a path) without breaking completions for learners who took the earlier version.
* Allowing prerequisites and compliance checks to respect both direct completions and alternate or equivalent completions.
* Recording clearly, in transcripts and reports, whether a training was completed directly or satisfied via an alternate relationship, along with which training served as the source.

### How the feature works conceptually

The feature is built on three main ideas: **relationships**, **alternate completion**, and **downstream behavior**.

#### Relationships between trainings

Administrators define relationships between courses and Learning Paths. For each relationship, they choose a **source** and one or more **targets**. A single course might have up to 30 targets depending on how many earlier or related trainings it should satisfy.

For Equivalence, admins can make the relationship **bidirectional** if they want both trainings to satisfy each other. For Alternates, admins normally keep the direction one*way to reflect that only some substitutions are allowed.

These relationships are stored at the training level, not at the learner level. Once configured and enabled, they apply to all current and future completions of the source training, subject to account*level settings such as whether retroactive completion is enabled.

### Alternate completion

When a learner completes a source training, ALM examines all configured alternate or equivalent relationships and, for each relevant target training, creates an **alternate completion record**. This record is distinct from a normal completion:

* It marks the target training for the learner but keeps track that it was completed via alternate or equivalence rather than directly.
* It records which source training was used to satisfy the target.
* It is stored in a dedicated structure so reporting can distinguish between direct and alternate completions.

Learners will see alternate completion even if they're not enrolled. The Learner Transcript (LT) report includes only records of trainings that the learner has enrolled in.

### Learner app experience for alternate and equivalent completions

Alternate and equivalent completions are surfaced distinctly in the learner app so learners can clearly understand how a training requirement was satisfied, while maintaining consistency with transcripts and reports.

#### LO card behavior

#### Alternate completion status

When a learner completes a training via an alternate or equivalent relationship, the Learning Object (LO) card displays a distinct status such as **Completed via Alternate**.  
This visual distinction helps learners differentiate between direct completions and completions granted through configured relationships.

#### Completion method indicator

The LO card includes a completion method indicator (for example, a label or icon) to show that the completion was achieved through an **Alternate**.  
If an alternate completion is later revoked due to changes such as retroactive incompletion or deletion of the source training, the LO card updates to reflect **Alternate (Revoked)**.

#### Transparency and audit details

Learners can open the LO card to view additional details, including:

* The source course or learning path that granted the alternate completion
* The completion date associated with the source training  

This ensures transparency and supports audit and compliance reviews.

#### Filtering and views

#### Completion method filter

The learner app provides a filter that allows learners to distinguish between:

* **Direct** completions
* **Alternate** completions
* **All** completions  

This enables learners to quickly understand how their learning requirements were fulfilled.

#### Transcript and progress views

The completion method filter is available in learner*facing views such as:

* Learning transcripts
* Progress and completion tracking sections  

These views clearly indicate which trainings were completed directly and which were satisfied through alternates or equivalence.

#### Reporting alignment

The filtering logic in the learner app aligns with the **Completion Method** column used in reports.  
This ensures consistency between what learners see in the UI and what administrators see in exports and compliance reports.

#### End*to*end flow

#### For learners

1. Navigate to **My Learning** or **Completed Courses** in the learner app.
2. Review LO cards to identify trainings marked as **Completed via Alternate**.
3. Open an LO card to view details about the source training and completion date.
4. Use the filter menu in transcript or course list views to select **Direct**, **Alternate**, or **All**.
5. Review the updated list based on the selected completion method.

#### For administrators and authors

1. Configure equivalent or alternate relationships between courses or learning paths in the admin interface.
2. Verify that alternate completions are correctly reflected on LO cards and in learner*facing filters.
3. Use learner views and reports to confirm consistency between UI and exported data.
4. If a source training is retired or deleted, validate that affected LO cards update accordingly (for example, showing **Alternate (Revoked)** when applicable).

## Retroactive completion and incompletion behavior

ALM supports retroactive completion and retroactive incompletion to ensure that alternate and equivalent relationships remain accurate over time, even when relationships are created, modified, or removed after learners have already completed training.

### Retroactive completion

#### Definition

When retroactive completion is enabled, learners who completed a source course in the past automatically receive an alternate completion for the target course if an equivalent or alternate relationship is created later.  
This ensures that historical learning is honored without requiring learners to retake training.

#### How it works

1. An administrator enables retroactive completion at the account level.
2. The administrator defines an equivalent or alternate relationship between a source and target training.
3. The system scans historical completion records for the source training.
4. Eligible learners are granted alternate completion for the target training.
5. These records appear as **Completed via Alternate** in learner transcripts and reports.

### Retroactive incompletion

#### Definition

When retroactive incompletion is enabled, alternate completions are revoked if the underlying equivalent or alternate relationship is removed or if the source training is deleted.  
This ensures the system reflects the current and valid training relationships.

#### How it works

1. An administrator enables retroactive incompletion at the account level.
2. The administrator removes an alternate or equivalent relationship, or deletes the source training.
3. The system identifies learners who received alternate completion through the affected relationship.
4. The corresponding alternate completion records are revoked.
5. Revoked records are marked as **Alternate (Revoked)** in transcripts and reports for audit visibility.

### Impact on prerequisites

Alternate completions—including those granted retroactively—are treated as valid completions when evaluating prerequisites.  
If a learner has **Completed via Alternate**, they are allowed to proceed with courses that require the target training.

If an alternate completion is later revoked through retroactive incompletion, the learner may lose eligibility for courses that depended on that prerequisite.

### Impact on learning paths and certifications

Alternate completions contribute toward progress and completion of learning paths and certifications.  
Learners can advance or complete these programs when required trainings are satisfied via alternate or equivalent relationships.

If an alternate completion is revoked, affected learning paths or certifications may lose progress or completion status until the requirement is met through a valid completion.

### End*to*end workflow

#### Enabling retroactive completion or incompletion

1. Administrators navigate to account settings and enable retroactive completion and/or retroactive incompletion.
2. Administrators create, modify, or remove equivalent or alternate relationships between trainings.

#### System actions

* **For retroactive completion:**  
  The system grants alternate completions based on historical source completions.
* **For retroactive incompletion:**  
  The system revokes alternate completions when relationships are removed or source trainings are deleted.

#### Learner experience

Learners see updated completion statuses on LO cards and in transcripts, such as:

* **Completed via Alternate**
* **Alternate (Revoked)**  

Prerequisite checks, learning path progress, and certification status update dynamically based on the current completion state.

#### Reporting and audit

All retroactive changes are reflected in the Learning Transcript (LT) report.  
Reports clearly distinguish between direct completions, alternate completions, and revoked alternate completions to support compliance, support investigations, and audits.

### Retroactive completion and incompletion behavior

ALM supports retroactive completion and retroactive incompletion to ensure that alternate and equivalent relationships remain accurate over time, even when relationships are created, modified, or removed after learners have already completed training.

#### Retroactive completion

#### Definition

When retroactive completion is enabled, learners who completed a source course in the past automatically receive an alternate completion for the target course if an equivalent or alternate relationship is created later.  
This ensures that historical learning is honored without requiring learners to retake training.

#### How it works

1. An administrator enables retroactive completion at the account level.
2. The administrator defines an equivalent or alternate relationship between a source and target training.
3. The system scans historical completion records for the source training.
4. Eligible learners are granted alternate completion for the target training.
5. These records appear as **Completed via Alternate** in learner transcripts and reports.

#### Retroactive incompletion

#### Definition

When retroactive incompletion is enabled, alternate completions are revoked if the underlying equivalent or alternate relationship is removed or if the source training is deleted.  
This ensures the system reflects the current and valid training relationships.

#### How it works

1. An administrator enables retroactive incompletion at the account level.
2. The administrator removes an alternate or equivalent relationship, or deletes the source training.
3. The system identifies learners who received alternate completion through the affected relationship.
4. The corresponding alternate completion records are revoked.
5. Revoked records are marked as **Alternate (Revoked)** in transcripts and reports for audit visibility.

#### Impact on prerequisites

Alternate completions—including those granted retroactively—are treated as valid completions when evaluating prerequisites.  
If a learner has **Completed via Alternate**, they are allowed to proceed with courses that require the target training.

If an alternate completion is later revoked through retroactive incompletion, the learner may lose eligibility for courses that depended on that prerequisite.

#### Impact on learning paths and certifications

Alternate completions contribute toward progress and completion of learning paths and certifications.  
Learners can advance or complete these programs when required trainings are satisfied via alternate or equivalent relationships.

If an alternate completion is revoked, affected learning paths or certifications may lose progress or completion status until the requirement is met through a valid completion.

#### End*to*end workflow

#### Enabling retroactive completion or incompletion

1. Administrators navigate to account settings and enable retroactive completion and/or retroactive incompletion.
2. Administrators create, modify, or remove equivalent or alternate relationships between trainings.

#### System actions

* **For retroactive completion:**  
  The system grants alternate completions based on historical source completions.
* **For retroactive incompletion:**  
  The system revokes alternate completions when relationships are removed or source trainings are deleted.

#### Learner experience

Learners see updated completion statuses on LO cards and in transcripts, such as:

* **Completed via Alternate**
* **Alternate (Revoked)**  

Prerequisite checks, learning path progress, and certification status update dynamically based on the current completion state.

#### Reporting and audit

All retroactive changes are reflected in the Learning Transcript (LT) report.  
Reports clearly distinguish between direct completions, alternate completions, and revoked alternate completions to support compliance, support investigations, and audits.

### Webhooks for equivalents and alternates

ALM provides dedicated webhook events for equivalent and alternate completions to support automation, integrations, and synchronization with external systems.

These events allow external consumers to reliably distinguish between direct completions and completions granted through alternate or equivalent relationships.

#### Overview

When a learner completes a course via an alternate or equivalent relationship, ALM triggers a webhook event that is separate from the standard course completion webhook.  
This ensures that integrations can respond differently to alternate completions where required.

Webhook events are also triggered when retroactive completion or retroactive incompletion occurs, covering historical updates as well as relationship changes.

#### Webhook event behavior

* A distinct webhook event is triggered when a learner receives **Completed via Alternate** status for a target course.
* The event is generated when the learner completes a configured source course that satisfies the target through an equivalent or alternate relationship.
* This webhook is not triggered for direct course completions.
* When retroactive completion or retroactive incompletion is enabled, webhook events are emitted for each affected learner and target course.

#### Webhook payload details

The alternate completion webhook payload includes the following key attributes:

* **Learner ID**  
  Identifies the learner who received the alternate completion.

* **Source course**  
  The course or learning path that the learner completed directly.

* **Target course**  
  The course that is marked as completed via the alternate or equivalent relationship.

* **Completion method**  
  Indicates that the completion method is **alternate**.

* **Completion date**  
  Derived from the completion date of the source course.

* **Relationship type**  
  Specifies whether the relationship is **equivalent** or **alternate**.

For retroactive incompletion scenarios, webhook events indicate that an existing alternate completion has been revoked.

#### Integration considerations

External systems can use these webhook events to:

* Update learner records
* Synchronize completion status
* Trigger notifications or downstream workflows
* Maintain audit trails for compliance purposes

Webhook consumers should explicitly differentiate between **direct** and **alternate** completions.  
Alternate completions do not grant skills, badges, or gamification rewards and should be handled accordingly in downstream systems.

### Impact of retiring and deleting source training in equivalents and alternates

The lifecycle state of a source training (retired or deleted) directly affects how alternate and equivalent completions are maintained for learners. ALM handles these scenarios differently to preserve historical accuracy while ensuring current relationships remain valid.

#### Retiring source training

##### Definition

Retiring a course makes it unavailable for new enrollments while keeping it in the system for historical reference, reporting, and audit purposes.

##### Impact

* Existing alternate completions granted through the retired source course remain valid.
* Learners who previously completed the source course continue to hold alternate completion for the target course.
* No new alternate completions are generated from the retired course, since it cannot be completed by new learners.
* Learner transcripts and reports continue to display **Completed via Alternate** for affected learners.

#### Deleting source training

#### Definition

Deleting a course removes it entirely from the system, including its completion records and configured relationships.

#### Impact

* If retroactive incompletion is enabled, all alternate completions granted through the deleted source course are revoked.
* Learner transcripts and reports update to show **Alternate (Revoked)** for audit and compliance visibility.
* Learners may lose progress or completion status in learning paths, certifications, or prerequisites that depended on the revoked alternate completion.
* No further alternate completions can be granted from the deleted course.

#### Workflow

1. An administrator retires or deletes the source course using the admin interface.
2. The system evaluates all alternate and equivalent completions derived from the source course.
3. Completion status is updated based on the course state:
   * **Retired:** Existing alternate completions remain unchanged.
   * **Deleted:** Alternate completions are revoked if retroactive incompletion is enabled.
4. Learner transcripts and reports reflect the updated status to support compliance and audit requirements.

### No chaining of relationships

ALM does not support chaining of alternate or equivalent relationships. Alternate completions are granted only for directly configured relationships and do not cascade across multiple levels of courses.

#### Concept: no chaining of relationships

#### Definition

Chaining refers to allowing alternate or equivalent relationships to propagate across multiple courses.  
For example, if Course A is an alternate for Course B, and Course B is an alternate for Course C, chaining would imply that completing Course A grants completion for Course C.

#### Policy

Chaining is not supported.  
Alternate and equivalent relationships are evaluated only at a single level. Completing a source course grants alternate completion only to its immediate target course or courses, not to any downstream targets.

#### Workflow

#### Relationship setup

An administrator defines alternate or equivalent relationships between courses, such as:

* Course A → Course B
* Course B → Course C

#### Completion event

A learner completes Course A directly.

#### System action

* The system grants alternate completion for Course B, if the A → B relationship is defined.
* The system does not grant alternate completion for Course C, even if a B → C relationship exists.

#### Direct completion requirement

To receive alternate completion for Course C, the learner must:

* Directly complete Course B, or
* Complete a course that is explicitly configured as a direct alternate or equivalent for Course C.

### Implications

#### No indirect benefits

Learners cannot receive completion credit for courses further down a relationship chain unless each course (or its direct alternate) is completed.  
This ensures that learning requirements are met explicitly and predictably.

#### Simplified audit and reporting

Reports and learner transcripts display alternate completions only for direct relationships.  
This avoids complex, multi-hop audit trails and ensures clarity when reviewing how a completion was granted.

### Catalog sharing with peer accounts: relationships not shared

Catalog sharing allows learning objects (LOs) to be shared across peer accounts, but alternate and equivalent relationships are managed independently within each account and are not shared.

#### Concept: catalog sharing and relationships

#### Catalog sharing

Accounts can share catalogs with peer accounts to provide access to courses, learning paths, and other learning objects across accounts.

#### Relationships not shared

Alternate, equivalent, and alternate-completion relationships configured in the source account are not shared or replicated when a catalog is shared.  
Each account maintains and evaluates its own relationships independently.

### Workflow

#### Catalog sharing

An administrator in **Account A** shares a catalog containing learning objects with **Account B**.

#### Relationship configuration

Account A may have alternate or equivalent relationships defined among the learning objects in the shared catalog.

#### Peer account access

Account B receives access to the shared learning objects but does not inherit any alternate or equivalent relationships configured in Account A.

#### Independent management

If Account B requires similar alternate or equivalent behavior, an administrator in Account B must manually configure the relationships within that account.

#### Implications

#### No automatic relationship propagation

Alternate and equivalent relationships are not automatically available in peer accounts through catalog sharing.

#### Manual setup required

Each peer account is responsible for defining and managing its own relationships for shared learning objects.

#### Consistency considerations

Completion behavior, prerequisite satisfaction, and reporting may differ across accounts unless relationships are intentionally aligned through manual configuration.


### Downstream behavior

Once an alternate completion exists for a target training, ALM uses it in downstream checks:

* If the target training is a **prerequisite** for other trainings, the learner becomes eligible for those trainings as if they had completed the target.
* If the target is a **mandatory course in a learning path**, the path's completion logic can treat the learner as having completed that part and proceed to mark the path complete when other conditions are met.
* Compliance and other dashboards such as Group Success Dashboard that rely on whether a training requirement is met can include learners who only have alternate completions.

The system distinguishes between actual completion and alternate completion so that:

* If the learner later takes the target training directly and completes it, this direct completion can override the need for the alternate completion.
* If the relationship between source and target is removed or changed, ALM can remove or adjust the alternate completions without touching genuine completions, provided retroactive incompletions are enabled for the account.

Alternate completions are designed not to interfere with actual learner activity on the target training. They act as an overlay that can be revised if the relationships change.

## Changes to Learning Transcripts report in this release

### Completion Method column 

The Completion Method column indicates how each record in the administrator's Learner Transcript was completed.  

Values: 

* Direct (for direct completions) 
* Alternate (for completions achieved via alternate relationships) 
* Alternate Revoked (when all alternate completions are revoked due to retroactive incompletion and relationship removal)

>[!NOTE]
>
>This column is not visible in the learner's LT; it is only available in the admin LT for reporting and tracking purposes.

#### Impact

Enables clear audit trails, compliance tracking, and transparency for admins regarding how a course was completed.

### Alternate completion tracking in Learner Transcripts

Alternate completions allow learners to receive completion credit for a target course or learning path when they have completed an equivalent source course or path, based on established relationships.  

In the Learner Transcript (LT), alternate completions impact three existing columns: status, completion date, and completion source:

* **Status**: The status can be Completed even if the learner has not directly completed the target course/path, due to alternate completion. Other statuses (Not Started, In Progress, Unenrolled) are not affected by alternates. Only Completed is impacted by alternates.
* **Completion Date**: The completion date for an alternate completion is inherited from the source course/path that triggered the alternate completion. If the learner later completes the target directly, the date is updated to reflect the direct completion.
* **Completion Source**: This column captures the training ID(s) of the source course(s) or path(s) that provided the alternate completion. If multiple sources are active, all relevant IDs are listed; if sources are revoked (with retroactive incompletion enabled), only active sources remain. The Completion Source column lists all active source training IDs (separated by commas), and if multiple sources exist, the earliest completion date is used.

#### Impact

Alternate completions reduce manual reconciliation, automate progress tracking in learning paths and certifications, and support compliance requirements.

>[!NOTE]
>
>Learner Transcripts do not display the Completion Method column; this is only available in administrator LT.

### Completion date logic for alternates  

The Completion Date column in the Learner Transcript (LT) is an existing field used to record when a learner achieves completion for a course or learning path, whether by direct or alternate means. For alternate completions, the completion date is inherited from the source course or path that triggered the alternate completion. This means the date reflects when the learner completed the source, not the target.  

If a learner later completes the target course or path directly, the completion date is updated to the date of direct completion, overriding the previous alternate completion date.  

There is no new column added for alternate completion dates; the existing Completion Date column is used for both direct and alternate completions. In cases where multiple sources can provide alternate completion for a target, the earliest active alternate completion date among the sources is used. If a source is revoked (with retroactive incompletion enabled), the completion date updates to the next earliest active source or is cleared if no active sources remain.

#### Impact

The completion date logic ensures accurate historical tracking and consistency in reporting, especially when alternate completions are revoked or updated.

### Revoked alternate completions  

Revoked alternate completions occur when a learner's alternate completion for a target course or learning path is removed due to the revocation of all source relationships, provided that retroactive incompletion is enabled in the account.  

#### Trigger conditions

* Retroactive incompletion must be enabled for the account; otherwise, removing source relationships does not revoke alternate completions.  
* Revocation happens only when all active source relationships for a target are removed. If at least one source remains, the alternate completion persists, and the completion source column updates to reflect only the remaining active sources.

#### Impact

* Status: If all alternate completions are revoked and there is no direct completion, the status is updated (e.g., from Completed to Not Started or In Progress as appropriate).  
* Completion Date: The completion date is cleared if no active sources remain and the learner has not completed the target directly.  
* Completion Source: The completion source column is updated to remove the revoked source(s); if all are revoked, it is cleared.

If the learner has a direct completion, revoking alternates does not affect their completed status or completion date.

**Note**:

1. If multiple sources provided alternate completion and only some are revoked, the LT reflects the remaining active sources and their earliest completion date. 
2. If all sources are revoked, and there is no direct completion, the learner loses completion status for the target.

### Enhanced reporting for checklist reviewer remarks

Reviewer comments from checklist modules are now included in Learner Transcripts (LT) under a renamed column: **Reviewer's remarks** (previously Submission comment).

#### Impact

Learners and admins can view consolidated, clearly labeled reviewer feedback in LT exports (UI, Job API, and connectors), improving transparency, auditability, and supporting more accurate performance evaluation and coaching.

#### What has changed

**Renamed columns**

| Area                        | Old column name    | New column name    | Notes                                                     |
| --------------------------- | ------------------ | ------------------ | --------------------------------------------------------- |
| Learner Transcripts (Admin) | Submission comment | Reviewer's remarks | Applies to all Admin LT sources: UI, Job API, Connectors, wherever applicable. |

This change applies uniformly to all Admin LT sources (UI exports, Job API reports, and Connector‑based exports, wherever applicable). Connector‑exported LT will surface Reviewer's remarks as a dedicated column at the end (for connectors that did not previously expose Submission comment), ensuring downstream integrations can distinguish reviewer feedback from other comments.

>[!NOTE]
>
>For the Learner Transcripts for learners, the column previously labeled "Submission comment" is now renamed to "Reviewer's remarks", and populated with the checklist reviewer's comment when enabled.



### Improved learning time calculation 

The LT report now uses a refined logic to distinguish between active and idle time spent on learning modules, based on user activity and tab focus. 

#### Impact

Provides more accurate measurement of learning engagement, supporting compliance and analytics.  
-->