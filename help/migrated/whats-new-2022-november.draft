---
title: What's new in this release (November 2022)
description: Learn about the new features and enhancements in Adobe Learning Manager
hidefromtoc: yes
exl-id: 2ccfb4e6-ba11-4657-8edb-3c527b4e5b9f
---
# What's new in this release (November 2022)

<!--
IN-PROGRESS

<https://helpx.adobe.com/learning-manager/whats-new-nov-2022.html>
-->

## Multiple SSO Configuration

Adobe Learning Manager currently supports one login method for internal and one login method for external users. This creates limitations in cases where customers have their employees and their own customers and channel partners on the same account.

With the intent to support multiple types of user groups logging into the platform, Adobe Learning Manager now supports multiple login methods through multiple SSO configurations for both internal and external users.

For more information, see [Multiple SSO logins](/help/migrated/administrators/feature-summary/multiple-sso-logins.md).

## Non-logged-in feature support

Adobe Learning Manager's native portal now supports non-logged in way of accessing a training portal.

Learners can now discover and access the training site, check out various courses and content available, and decide to log in to consume the courses.

This feature makes it easier to create a customer-facing learning portal, where learners can browse various courses without being logged in initially.

For more information, see [Non-logged in experience for learners](/help/migrated/administrators/feature-summary/non-logged-in-experience-learners.md).

## Training Overview Page Enhancements

The Training Overview page now sports a refreshed UI so that learners have an enhanced experience while consuming a course.

Other enhancements include:

* Bookmark a training.
* Recommendation of related courses.
* Learning Path (s) information for courses and Learning Paths.
* Clickable author names.
* Breadcrumbs for easier navigation.

## Training Overview Page Enhancements

The Training Overview page now sports a refreshed UI so that learners have an enhanced experience while consuming a course.

Other enhancements include:

* Bookmark a training.
* Recommendation of related courses.
* Learning Path (s) information for courses and Learning Paths.
* Clickable author names.
* Breadcrumbs for easier navigation.

## Author Profile Page

The author profile page shows all the training that is created by a particular author.

Learners can easily find author-specific information, and all training created by the author.

## Bookmarked trainings

Learners can save (using the Save button) or bookmark training for them from the course tile or overview page. All bookmarked courses are available on the learner homepage.

## Player customization

In this release, you can customize the Fluidic Player to match the branding requirements of a course.

You can show and hide various player settings and options based on the content requirement and grant control to learners based on content type. You can apply this change to both native and headless implementations. 

The various options you can change include:

* Toggling table of content
* Notes
* Language
* Speed
* Caption
* Volume
* Playback controls

## Impersonation of Learner and Manager

Admins can launch an impersonated session where they can log in on behalf of any user in their account in their learner and manager role.

For more information, see [Impersonation of Learner and Manager](/help/migrated/administrators/feature-summary/impersonation-learner-manager.md).

## Other enhancements

### Audit log of Emails

Admins can now access all email logs sent from the system via an Email audit trail report.

This log captures all data related to emails sent in the last 30 days and gets refreshed every day. In addition, the report contains information, for example, delivered status, sender, receiver, subject, and content metadata.

Download the report from Reports > Custom Reports > Excel Reports > Emails Report. A notification appears via which you can download the report.

This report consists of the following fields:

* Email Triggered Time (UTC TimeZone)
* Last Event Status Time (UTC TimeZone)
* Delivery Status
* Receiver Email
* Sender User ID
* Email Subject
* Entity Type
* Entity Name
* Entity ID

### Waitlisted learner notification

When an author adds a new instance, the author can trigger an email to notify waitlisted learners of other instances. The learners get an email of the change. 

### Instance Level Email Templates

You can customize emails for each instance of a training.

Wherever the Author or Admin is allowed to add a new instance, the template for an individual instance can be edited.

For example, if a course has different audience types, you can change the email template accordingly. 

![email templates](assets/email-template.png)

The priority of the template is listed below:

1. Instance-level template
2. Training-level template
3. Account-level template

### Instructor comments while accepting submissions

Instructors can now add comments while accepting the submissions made by learners. The learner receives an email notification and an in-app notification (If enabled) once the submission is approved by the instructor. The submission-related comments are present in the Learner Transcripts for both Admin and Learner.

### Search-related enhancements

A learner's recent search history appears so that they can view all past searches.

The search results are now consistent across all formal and informal learning (social learning). The results include training, social learning, and content marketplace matches.

The search is more focused and targeted, where you can view the search results in three places, formal learning, social learning, and Content Marketplace.

![search](assets/search-image.png)

#### Phrase-driven search

In this release of Adobe Learning Manager, we've replaced Typeahead search with phrase-driven search.

#### Recent searches

A learner can view their recent searches in the current session only.

### Content marketplace free courses catalog

Out of the box, a set of curated, high-quality, free catalog of 50 complimentary courses is now available from the content marketplace for learners.

### Support for Indonesian language

Bahasa Indonesia is now added as an interface language in the learner and manager apps.

### Mandatory Author field

While creating a course, the Author field is mandatory.

### Content Marketplace changes

* Newly created trial accounts will list a new catalog for 50 free courses in the Content Marketplace, which are available for users.
* A learner can now see the number of search results and link embedded links for redirection to Content Marketplace.

### Mobile immersive changes

In this release, mobile immersive web users can perform the tasks, listed below:

* Create - Poll posts
* Edit post - all types, RTE
* E-commerce workflow.
* Preview a module: Learners will have the Module Preview feature in Mobile Immersive. This change will enable learners to preview the module before enrolment to a course.
* Copy a URL.
* Delete a board.

### Zoom connector changes

The JWT app type will be deprecated in June 2023. We recommend that you create Server-to-Server OAuth or OAuth apps to replace the functionality of a JWT app in your account.

### Report for gamification

In this release, you get access to a report that displays various courses where gamification was enabled.

### Import language preference via CSV

When importing a CSV, the CSV contains Interface Language, Content Language, and Time Zone as fields.

The Admin may also export the report, which contains the same fields as above.

* Interface Language
* Content Language
* Time Zone

Apart from Admins, a Custom Admin can also export this report.

![language report](assets/language-report.png)

#### Impact on localization

* The column names cannot be localized and must be as is (Interface Language, Content Language, Timezone).
* The locale codes are case-insensitive.
* While there is no restriction on providing the country code, you can specify only the language code. For example, both "it_IT" and "it" are valid.
* If there is any discrepancy in the report due to an incorrect locale code, the csv processing continues, as usual, and it does not impact the other records in the csv. The locale preference of the user with an incorrect locale does not get updated. The rest of the data gets updated.

## API changes and enhancements

### VC Connectors

If an admin email id is used to configure the VC connector, then that particular admin must have permission for the following:

* Creating a meeting
* Updating a meeting
* Fetching attendance report

While creating or updating the VC meeting, instructors must END the meeting within 30 minutes of the scheduled end time of the meeting.

### Bookmarking

The following APIs are added for bookmarking a course on the Training Overview page:

* Get all bookmarks: `primeapi/v2/bookmarks`
* Create a bookmark: `primeapi/v2/learningObjects/{id}/bookmark`
* Delete a bookmark: `primeapi/v2/learningObjects/{id}/bookmark`

### Support for multi-locale metadata and content through migration

For all types of training supported in the platform (course, learning paths, modules, certifications, and job aids), multiple language migration can now be supported via CSV files using extra columns for additional languages.

#### Prerequisites

Create the migration project as an Integration Admin and then share the migrationProjectId with the ALM support team, so that the multi-locale flag can be enabled from the backend.

#### Scope of multi-locale migration objects

* Module
* Course
* Module version
* Certification
* Learning program
* Job aid
* Job aid version

#### CSV specification

Adobe Learning Manager provides you with a set of standard CSV specifications for Multi locale-enabled migration. The best practice is to go through these CSV specifications before starting with the migration process. The Integration Administrator of your organization can analyze the existing data formats and map them to match with the Learning Manager-provided CSV template items.

#### Changes with multi-locale support

* The module_version column is not supported in module_version.csv and course_module.csv.
* Cannot update the module_version in the same run (in the same run, the module cannot be migrated with two versions with the same module).
* Content or metadata update is considered as module version update from module_version.csv.
* Cannot support Job_Aid_Version update through job_aid_version.csv

### Revoke auth tokens and cookie

A headless LMS application gets hold of refresh_token up on first login. Afterwards, the refresh_token is used for generating access_token for its client applications to make API calls. Similarly, content playback uses oauth endpoint to generate cookie for managing playback which involves multiple content files and api calls invoked by those files using cookie. The cookie that is generated by oauth has same validity as the access_token which is seven days. Once the cookie is generated, there is no way to clear it unlike typical web application logout. The Oauth cookie and web application cookie are two different cookies and are not aware of each other.

So, to clear the cookie, we've introduced a new endpoint, which revokes refresh_token, cookie, and both cookie and refresh token.

**Details**

**Endpoint**

`POST oauth/o/revoke` 

**Query parameters**

* `cookie=true|false` - indicates that cookie needs to be revoked
* `refresh_token=true|false` - indicates that refresh

**Request body**

Body required for revoking refresh_token or (refresh_token and cookie)

```
{
      "client_id": <>,
      "client_secret": <>,
      "refresh_token": <>
}
Body required for revoking oauth cookie only
{
      "access_token": <>
}
```

### APIs made public

In this release, we've made a few APIs public.

| API | Type | Description |
|---|---|---|
| /social/search | GET | Search in social. |
| /announcements | GET | Get detailed information about the announcement on the masthead that is assigned to the learner. |
| /announcements/`{id}` | GET | Get detailed information about the announcement on the masthead that is assigned to the learner. |
| /learningObjects/`{id}`/loResources/{loResourcesId} | GET | Upload url of the file for loResource of resourceType 'Activity' where file submission is required. |
| /jobAid/`{jobAidId}`/jobAidDownloaded | GET | Set job aid download report. |
| /bulkimport/startrun | POST | Run bulk import. |
| /bulkimport/cansync | GET | Sync bulk import. |
| /search | GET | DELETEMEBOB |
| /uploadInfo | GET | Get content update related information. |
| /uploadSigner | GET | Get signature of the to_sign content. |
| /avatar | POST | Updates the learner's avatar image with a new image. |
| /avatar | DELETE | Deletes the learner's avatar image. |

### Salesforce app

The **Ignore higher Order LO** option must be enabled in the Salesforce app so that all the courses, Learning Programs, and Certificates can be viewed at the same time. 

### APIs for player customization

In this release, we've provided APIs to customize a player. You can:

* Start or load the player.
* Navigate to a particular module.
* Toggle Table of Contents.
* Change language.
* Close the player.
* Play, pause, forward, backward, seek, change volume, or change speed.
* Capture events emitted from the player.

### Show the waitlist position of a learner

The GET /enrollments/{id}/waitlistPosition API under LO API retrieves the waitlist position of a user for a specified enrolment.

### Completion date submission in external certifications

The /primeapi/v2/learningObjects/certification:xxxxx API will have "completionDateSameAsApprovalDate" attribute to indicate that the cert has "Certification Completion Date" enabled for learner or not along with true/false flag.

### Get LO preview data

The GET /preview/learningObjects/{id} API is added to  Get preview information about a learning object.

### Move external users within profiles

The `PUT primeapi/v2/externalProfiles/{currentep}/users/{userid}?` call helps move a user to another external profile by specifying a new externalProfile id.

### Add users to external profiles

The `POST /externalProfiles/{id}/users` adds external users into external profile.

## Release Notes

For information regarding current and previous releases of Learning Manager web app and device app, see the [Release notes](/help/migrated/release-note/release-notes.md).

## Bug fixes

To see the bugs that are fixed in this update, refer to the [Bugs fixed list](release-note/release-notes.md#bugs-fixed-in-this-release).

## System Requirements

[Learning Manager system requirements](/help/migrated/system-requirements.md)
