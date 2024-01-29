---
description: Learn about the new features and enhancements in Adobe Learning Manager
jcr-language: en_us
title: New features summary
contentowner: jayakarr
---


# New features summary {#new-features-summary}

Learn about the new features and enhancements in Adobe Learning Manager

The April 2020 release of Adobe Learning Manager consists of performance enhancements, API changes, manager workflows, social learning, reporting, bug fixes, and other enhancements. Read on to know more about the changes in this release.

# Performance {#performance}

This release focuses on performance and scalability of the entire platform. This release includes several architecture-level enhancements to boost the performance and reliability of the platform. Some of the areas where Administrators and Learners should see improvements are:

* **Synchronous completion:** Sometimes learners used to experience a delay of few seconds in getting their training marked as completed. Learners can now see the completion information as soon as the training is completed.
* **Faster bulk workflows:** Workflows like enrollments, unenrolments, mark-completion for many users in bulk are now processed faster. Enrollments are five times as faster depending on the scenario.
* **Faster email processing:** Emails are now processed faster. This means that users get their emails, like enrollment emails, reminder emails sooner once the action is triggered.

# Classroom training {#classroom}

* In the **Learner** page of the Instructor app, learners are now displayed in an ascending order. The list is also reversible. If the list is downloaded as PDF, the order is maintained.
* As an Admin, you can now export the attendance details of a training as a PDF. For  more information, see [***Export attendance***](administrators/feature-summary/courses.md#attendance). The session time mentioned in the Learner list PDF (roster sheet) for instructors was always in UTC. Now the session time is displayed as the time zone in which the session is configured.
* To avoid duplicate names, a learner’s email id now displays as tooltip in the instructor app.

# Manager workflows {#manager}

* If a user enrolls to any manager-approved courses, the user can unenroll himself/herself. If the learner is in a pending state, he/she can unenroll and enroll in other instances of the course. The manager gets a notification for approval or rejection of the course or instance of the course. The manager gets a message, “**Learner has canceled the enrollment request**”, when the manager tries to approve/reject the course.
* In this release, learners can specify the correct completion date for external certifications. In previous versions, the completion date was set by default, based on the date of approval from the manager. Completion date provided by the learner should be greater than the certificate creation date. For more information, see [***Certification***](administrators/feature-summary/certifications.md).

# Social learning {#social}

* A learner who also has an admin role can add a user group to a private board. Any user group can be added to the private board and the users belonging to the user group only has access to the board. For more information, see  [***Board visible only to selected users***](learners/feature-summary/social-learning-web-user.md#selected-users).  

* Admins can add dynamic user groups while setting up private boards. For more information, see [***Set up a private board***](learners/feature-summary/social-learning-web-user.md#createboard).  

* Posting in social has increased word limits- 4000 for a post, 1000 for a comment, and 1000 for a reply.

# Reporting {#reporting}

* Custom Admins and Administrators can now download gamification reports, which wasn’t the case in earlier versions. The Gamification transcript now contains the gamification level the user is at, and the date on which the user had achieved the level.  The dates for the levels achieved would appear only if a learner completes any activity after this release. For more information, see  [***Add gamification report to a custom role***](administrators/feature-summary/custom-role.md#gamification-custom).
* Learning Manager now provides Administrators a history of the learner transcript downloads requests performed in the account. This allows Administrators to see historical requests,download the same transcript again from an already completed request, and even cancel a '**Queued**' or an '**In progress**' request if required. For more information, see  [***History of Learner Transcript downloads***](administrators/feature-summary/learner-transcripts.md#ltdownload).

# Learner experience {#learner}

* In the **Tags** panel on the left in My learning and Catalog pages, tags now display alphabetically.
* If a course contains an eLearning content that is the first content of the course, the course launches as soon as a learner enrolls to it. The learner need not click Start to launch the content after enrolling.

# Administrator app {#administratorapp}

Learning Manager already supports Adobe Connect’s persistent rooms. With this release, Admins/Authors can now create multiple instances of a single VC course using different persistent rooms for each session. Earlier only one already selected persistent room was available while setting up newer instances as well.

For more information, see  [***Changes to the Course Instance page for Connect VC modules***](authors/feature-summary/courses.md#connect-vc).

# Migration {#migration}

Through migration, content type AUDIO is now supported. The file module_version.xlsx now mentions AUDIO as content type. Similarly, AUDIO as content type is specified in the file job_aid_version.xlsx.

The content can be updated both as module or job aid.

* In module_version.csv, content type AUDIO is now supported.
* In job_version.csv, content type AUDIO is now supported.

Download the csv files from the [***migration manual***](integration-admin/feature-summary/migration-manual.md).

# Other enhancements {#otherenhancements}

* Search for any skill by typing the name of the skill and choosing the skill from the options present. Type-ahead search is also applicable here.. For more information, see [***Search a skill***](administrators/feature-summary/skills-levels.md#searchskill).  

* On the Manager Dashboard, a manager can view his/her pending tasks, so that he/she can take actions accordingly.

# New and changed APIs {#api}

## Stats {#stats}

The **stats** API helps you to fetch summary information for a specified LO Instance. The summary information includes the following:

* Number of enrollments.
* Number of completions.
* Number of waitlisted learners.

**Response**

```
\{ 
 "links":{ 
 "self":"http://localhost:8080/primeapi/v2/learningObjects/course:874326/instances/course:874326_1087084/summary" 
 }, 
 "data":{ 
 "id":"course:874326_1087084_summary", 
 "type":"loInstanceSummary", 
 "attributes":{ 
 "completionCount":0, 
 "enrollmentCount":1, 
 "waitlistCount":0, 
 "seatLimit":0 
 } 
 } 
}
```

## Jobs {#jobs}

The Jobs API allows an API client to create a Job and fetch the results for that job asynchronously. 

In this release, we have implemented a new job to get the list of all users in an account in CSV form along with active fields. The following fields are now available:

* internalUserID
* customerDefinedUniqueUserId
* userEmail
* name
* managerEmail
* userType
* profile
* roles - available as JSON
* Active fields - each active field will come as a column with prefix AF_
* metadata - as json string
* dateCreated 
* lastLoginDate
* state
* excludedFromGamfication 
* pointsEarned
* uiLocale
* contentLocale
* timeZoneCode
* userSource - Possible values are ('CSV','SU','SR','ER')

## Learning object API {#learningobjectapi}

Till now learners were able to unenroll themselves from job aids alone. In this release, we have added support for unenrollment from other Learning Objects - courses, certificates, and Learning Programs.

The API below has been enhanced to accommodate the changes.

*DELETE/enrollments/{id}*

# Issues fixed in this release {#issuesfixedinthisrelease}

**API**

* The Patch user API was failing to update user data if the user has a custom role.

**Learner**

* A learner can view and enroll to courses in a Learning Program or Certification, even if these are not part of a catalog that is enabled. Now in this update, a learner cannot enroll in a course if the course does not belong to the catalog.
* When a learner comes back to the page My Learning, the check-box filters in the Type and Status sections remain enabled.
* A learner, after choosing an instance for a newly added course, is unable to select the course module and complete the Learning Program.
* Learners who are added to a Learning Program do not get session or calendar invites to the course that has been recently added to the Learning Program.

**Learning Objects**

* On the Learning Plan page with more than 1000 Learning Plans, the column Occurs when displays the message Error for all learning plans.

**Reporting**

* When a custom admin sets the frequency to Daily for a Learner Status, the report does not get generated as expected.
* In an auto-generated user group, if you update the name of a manager, the change does not happen as expected.

**Email templates**

* When an Admin disables the option Sessions Details For Classroom (Admin app > Email Templates > Reminders & Updates tab), a learner still receives mails regarding session updates, contrary to the expected behavior.
* Email templates for a course changes to default template when disabled or enabled. The changes made do not propagate as expected.

**Instructor**

* An instructor added to an activity module, cannot be removed from the Instances tab in the Admin and Author apps.

