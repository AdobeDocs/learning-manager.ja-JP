---
description: Learn about the new features and enhancements in Adobe Learning Manager
jcr-language: en_us
title: New features summary
contentowner: jayakarr
---


# New features summary {#new-features-summary}

Learn about the new features and enhancements in Adobe Learning Manager

## What's new in this release {#whatsnewandchanged}

<table>
 <tbody>
  <tr>
   <td><img src="assets/classroom1.jpeg"></td>
   <td>
    <p><b><a disablelinktracking="false" href="whats-new.md#classroom">Classroom</a></b><br></p></td>
   <td><img src="assets/gamification.jpeg"></td>
   <td>
    <p><b><a disablelinktracking="false" href="whats-new.md#gamification">Gamification</a></b></p></td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><img src="assets/teams.jpeg"></td>
   <td>
    <p><b><a disablelinktracking="false" href="whats-new.md#teams">Microsoft Teams</a></b></p></td>
   <td><img src="assets/api.jpeg"></td>
   <td>
    <p><b><a disablelinktracking="false" href="whats-new.md#api">API changes</a></b></p></td>
  </tr>
 </tbody>
</table>

## Classroom locations

Administrators can now set up a library of classroom locations. For each Classroom Location, the administrators can set the metadata that includes Location Name, Seat Limit as well as additional information such as the Location URL. Authors and Administrators can then use these pre-configured classroom locations for setting up instructor-led training events (classroom modules).

For more information, see [**Classroom in Adobe Learning Manager**](administrators/feature-summary/classroom.md).

## Gamification

In this release, Adobe Learning Manager introduces a new gamification task that encourages users to access the learning platform consistently and engage in the learning activities. To support this task, the Administrator can now setup a new rule that awards points if the learner carries out learning activities for 1, 2, 3, or 4 days in a week, month, or quarter.

For more information, see [**Gamification**](learners/feature-summary/gamification.md).

## Microsoft Teams connector

Microsoft&reg; Teams&reg; is a persistent chat-based collaboration platform that supports document sharing, online meetings, and other features for business communications.

Adobe Learning Manager uses a virtual classroom connector that can be used to integrate Microsoft Teams meetings into Learning Manager.

Microsoft Teams connector connects the Learning Manager and Microsoft Teams systems to enable automatic data synchronization.

For more information, see [**Install Microsoft Teams connector**](integration-admin/feature-summary/install-microsoft-teams-connector.md).

## Player TOC changes

## Performance improvements

This release of Adobe Learning Manager introduces significant performance enhancements for the fluidic player table of contents (TOC). Some of the changes include faster rendering of content, displaying course completion information in the TOC after the player is closed, displaying a tick mark in TOC after a module or course is completed, better support for the content types, such as PDF, video, and audio formats, and so on.

![](assets/player-toc.png)

## Accessibility improvements

We have made several accessibility enhancements to the fluidic player TOC. Few of these changes include support for better color and sharp contrast, as well as more prominent TOC labels.

## Search and sort modules

When an instructor has multiple sessions or submissions, searching for and sorting through these sessions and submissions can become difficult and tedious. With this release, the modules, and sessions available on the instructor page are now searchable using the name of a course, session, or module. Learning Manager now provides a search field that is available for all the upcoming sessions, past sessions, and review activities including checklists and submissions.

To search for a particular session or module name, follow the steps below:

1. In the Instructor app (UI for Instructor role), search for the upcoming and past sessions. You can view the list of instances for the selected page.
1. Enter the session or module name in the search field available at the upper-right corner.
1. Locate the learning object from the search results.

>[!NOTE]
>
>The search results show not only the courses or modules assigned to the instructor, but all the courses or modules that match the search criteria. Select the course or module to which you are assigned.****

To reset the search filter, you can use the **Clear** link available next to the course or module name.

![](assets/reset-search-filter.png)

## Set default Social Learning view for Learners

Previously, although only Administrators were permitted to enable and configure the Social Learning settings for a Learner, the post view was the only default option for viewing the social learning forum.

With this release, the Administrators can now change the default Social Learning view as per the preferences. The default post view can now be changed by utilizing the Social Learning dashboard view setting. The setting enables the Administrator to set the Learners' default Social Learning view to either post view or board view.

**Follow these steps to change the default Social Learning view for Learners**

1. In the Admin app, click **Social Learning** under **MANAGE **in the left pane.

1. In the **Settings **tab,** **click** Edit **for** Social Learning view. **You can see that by default, the system selects **Post View**.

1. Select one of these options to set your preferred default Social Learning view

   1. **Post View** — Displays all individual posts from all Discussion boards.
   1. **Board View** — Displays all Discussion boards.

1. Click **Save** to save the changes.

>[!NOTE]
>
>Although the Administrators can alter the Social Learning view, the selected default view preference remains in effect only until a Learner changes it. A Learner can change the view type overriding the default view setting (that is configured by the Administrator) by using the Social Learning page. However, the Social Learning view reverts to the default view type configured by the Administrator when you perform page-refresh or navigate away.

## Set default My Learning and Catalog view for Learners

For every Learner, by default, the Learning objects appear using the grid view. Previously, in the absence of a configurable setting, the Administrators could not change the default viewing preference for the learners to list view.

With this release, an Administrator can now set the Learners' default view type (for My Learning and Catalog pages) to list view. The objects such as available courses, learning paths, and certifications can now appear in a list view layout by default. The Administrator can now use the newly added setting to set the default view type for the Learners to either grid or list view.

Follow these steps to change the default view for Learners:

1. In the Admin app, click **Settings** under **CONFIGURE** in the left pane.

1. Click **General** under **BASICS** to access the General settings page.

1. Select the **List view** option alongside **Default view (Learner role)** to change the Learners' default view from Grid to List. If you clear **List view** option, the system sets the Learners' default view back to Grid.

1. After you select (or clear) the **List view** option, the system displays the following confirmation message.

After selecting **List view**, when a learner signs into the Learner app, by default, My Learning and Catalog pages appear using list view.

Although Administrators can alter the Learners' view, the selected default view preference remains in effect only until a Learner changes it. A Learner can override the default view preference for the My Learning and Catalog pages (that is configured by the Administrator) by switching between the Grid and List views.

## Mobile immersive web changes

## Social Learning

Social Learning now supports the mobile immersive web experiences.

![](assets/mobile-immersive.png)

## API changes

### Download all badges

#### GET jobs/

This is an admin API, using which the administrator can download a badge in the PDF format for a user or training.

#### Download all badges by training id

```
\{ 
 "data": { 
 "type":"job", 
 "attributes": { 
 "description":"description of your choice", 
 "jobType":"generateUserBadge", 
 "payload": { 
 "trainingId":"course: XXXX" 
 } 
 } 
 } 
}
```

There is pagination when downloading badges by training id. The maximum limit per page is 1000.

#### Download all badges by userid

```
\{ 
 "data": { 
 "type":"job", 
 "attributes": { 
 "description":"description of your choice", 
 "jobType":"generateUserBadge", 
 "payload": { 
 "userId":"1234" 
 } 
 } 
 } 
}
```

There is no pagination when downloading badges via userid.

## GET learningObjects for classroom management

This release features a change in the resource model. The relationships object has a new field named "*room*." This change is only applicable to a classroom module.

## Gamification API

The API includes the capability for awarding points for the external events.

**POST /users/externalGamificationPoint**

Request Body:

```
\{ 
 "userId": userId in the account 
 "eventTime": Time in "2020-01-01T18:30:00.000Z" format 
 "points": points earned; it should be < 100000 
 "source": Source where these points are achieved (String limited to 128 chars) 
} 

```

## Mark a board as favorite

If you want to mark a board as favorite, provide the board id.

*POST /boards/{id}/favorite*

## Report a board

If you want to report a board, provide the board id.

*POST /boards/{id}/reportAbuse*

## Remove a board from favorites

If you want to remove a board from favorites, provide the board id.

*DELETE   /boards/{id}/favorite*

## Board API changes

The field *isFavorite* is added in the model.

## Calendar API

*GET /users/{id}/calendar*

The following fields are added to the payload:

1. *courseInstanceName*
1. *courseName*
1. *enrolledToCourseInstance*
1. *"instructorNames": `["string"]`*

The *enrolled* and *enrolledToCourseInstance* fields are added to determine if a learner is enrolled to the course and if the learner is enrolled to the course instance in a calendar model.

`filter. allSession` is added in the query parameter to get all the sessions related to all instances and all sessions in a course.

The following fields are added in the relationship:

1. *instructors*
1. *Room*

## What's changed in this release {#Whatsnewandchanged-1}

## Workday enhancements

Here are the changes in this release:

* Workday&reg; supports a wide range of attributes to add data. Different organizations use these attributes differently. Therefore, exposing these attributes and allowing the Administrators to map them with Learning Manager would have increased product complexity and affected usability. If you want to map any attribute that is not listed in Learning Manager, contact your CSAM with the details. The CSAM Support team of Learning Manager will investigate the requirement and help you based on the technical feasibility.
* We have added a checkbox **Exclude Contingent Workers**. When you select this checkbox, the system does not import any temp workers available under a manager.

## Calendar widget enhancements

In the previous releases of Learning Manager, the Calendar widget consisted of the name and state of a course. Starting this release, the Calendar widget displays the session name, course name, course type, and the session time.

![](assets/calendar-widget.png)

The calendar widget now displays the session name first (with higher prominence) followed by the course name and other details.

Earlier the widget showed only one session from the entire course. The widget is now enhanced to show all the sessions from all the instances available in the course. This provides complete information for all sessions available in the course that enables the learner to enroll in any instance that they want.

When the calendar widget loads the next month, a loader icon now appears when the data is being fetched.

## Content language options

In this update, we added support for the following content languages:

* Serbian
* Slovenian
* Slovak

## Express interest

On the **Content Marketplace** page, the **Express Interest** button will now be disabled to prevent learners from expressing interest for a playlist/entire catalog for which they have already expressed interest.

## Language support in email templates

In this release of Learning Manager, we've added support for Hungarian and Finnish languages in email templates.

## Classroom enhancement API changes

`GET /users/{id}/calendar`

The following fields are added to the payload:

1. *courseInstanceName*
1. *courseName*
1. *enrolledToCourseInstance*
1. *`"instructorNames": ["string"]`*

>[!NOTE]
>
>The *enrolled* and *enrolledToCourseInstance* fields are added to determine if a learner is enrolled in the course and if the learner is enrolled in the course instance in a calendar model.

*`filter.allSession`* is added in the query parameter to get all the sessions related to all instances and all sessions in a course.

 The following fields are added in relationship:

1. *instructors*
1. *room*

The resources model corresponding to classroom module appears in the relationship.

## Deprecated features in this release

In this release, the `learningObject` in relationship of `learningObjectSkill` model has been deprecated. We have added a new key, `learningObjectId` in the attribute section of `learningObjectSkill` model to fetch the same information. The value corresponding to this key will be the id of learningObject. This change will affect the following LO types:

* Course 
* LearningPath (API terminology: learningProgram)
* Jobaid

The deprecated data will be completely removed from the response as a part of our next release. **This will take place after 3 months (anytime after 30 April 2022)**. Make the required changes to your implementation to fetch the data according to the the new design.

Here is a sample LO skill model:

```
Model: 

{ 
 "id": "course:5627858_51096" 
 "type": "learningObjectSkill", 
 "attributes": { 
 "credits": 19.7 
 "learningObjectId": "course:5627858" << new attribute added. 
 }, 
 "relationships": { 
 "learningObject": { 
 "data": { 
 "id": "course:5627858", 
 "type": "learningObject" 
 } 
 }, 
 "skillLevel": { 
 "data": { 
 "id": "51096_1", 
 "type": "skillLevel" 
 } 
 } 
 } 
 } 

```

We plan to change the ID format of learningObjectResourceGrade. The id format for the learningObjectResourceGrade model currently follows the following format:

* *course:courseid_instanceid_moduleid_version_uuid1_uuid2*

Once changed, the format will be:

* *course:courseid_instanceid_moduleid_version_uuid*

Thus, only one uuid will be used to construct the learningObjectResourceGrade's id.

In general, Learning Manager recommends to not interpret the ID of any model.

>[!NOTE]
>
>This change will come into effect as a part of our next release (any time after **30 April 2022**). In case you are using this format in any way, make the required changes. 

## Release Notes {#releasenotes}

For information regarding current and previous releases of Learning Manager web app and device app, see the  [***Release notes***](release-note/release-notes.md).

## Bug fixes {#bugfixes}

To see the bugs that are fixed in this update, refer to the  [***Bugs fixed***](release-note/release-notes.md#bug-fixes-jan-22) list.

## Known issues {#knownissues}

To see the known issues in this update, refer to [***Known issues***](release-note/release-notes.md#known-issues) list.

## System Requirements {#systemrequirements}

[Learning Manager system requirements](system-requirements.md)

<!--
## Previous releases of Learning Manager {#previousreleasesofcaptivateprime}

* [Learning Manager | October 2021 release](whats-new-october-2021.md)
* [Learning Manager | August 2021 release](whats-new-august-2021.md)
* [Learning Manager | February 2021 release](whats-new-february-2021.md)
* [Learning Manager | December 2020 release](whats-new-december-2020.md)
-->

## Have a question or an idea? {#haveaquestionoranidea}

<!--
Saurav:
This .svg file fails to render properly
-->

<table>
 <tbody>
  <tr>
   <td><img src="assets/ask-the-community.svg"></td>
   <td>
    <p>If you have a question to ask or an idea to share, come and participate in the <a href="https://community.adobe.com/t5/captivate-prime/bd-p/captivate-prime?page=1&amp;sort=latest_replies&amp;filter=all" disablelinktracking="false"><strong><em>Adobe Learning Manager Community</em></strong></a>. We would love to hear from you and address your queries.<br></p></td>
  </tr>
 </tbody>
</table>

### More like this

* [Adobe Learning Manager product guide](https://www.adobe.com/products/captivateprime.html)
* [Adobe Learning Manager playlist](https://www.youtube.com/playlist?list=PLq21ukQtk0URntzGmTxsx7Qt8z9b9Elth)
* [Organize your training in Adobe Learning Manager | Ashwini Jaisim](https://elearning.adobe.com/2020/07/organize-your-trainings-in-adobe-captivate-prime/)
* [Add your Adobe Learning Manager Account URL to your Adobe Connect Central Account Summary Page](https://elearning.adobe.com/2019/10/add-adobe-captivate-prime-account-url-adobe-connect-central-account-summary-page/)
