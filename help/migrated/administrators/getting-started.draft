---
description: This document provides a recommended approach for organizations to set-up and configure Adobe Learning Manager. Learning Manager team suggests a phased approach to get started with the application. It is not mandatory for you to follow all the phases in a specific sequence. 
jcr-language: en_us
title: Best practices guide to set up Learning Manager 
contentowner: jayakarr
preview: true
---


# Best practices guide to set up Learning Manager 

This document provides a recommended approach for organizations to set-up and configure Adobe Learning Manager. Learning Manager team suggests a phased approach to get started with the application. It is not mandatory for you to follow all the phases in a specific sequence.

These phases can be performed by three different roles, by one or more individuals based on your organization setup. The three roles are as follows:

1. **IT Administrator** -  IT Administrator performs activation or integration-related activities associated with Learning Manager application in an organization. IT Administrator can also add single/multiple users and perform a role of an Integration Administrator.
1. **Author** - Author creates learning content required for the organization's learning requirements. Author of training or learning content of your organization can start creating the basic content that is required for the Learning Manager application. 
1. **Learning Manager Administrator** - Learning Manager application Administrator performs configuration and set-up activities. In some companies, IT Administrator may also play a role as Learning Manager application administrator.

You can go through the infographic provided below to get an overview of the phases and corresponding tasks. 

![](assets/learning-manager-getting-started.jpg)

At this stage, we assume that your organization has already received the license key and you have activated the Learning Manager account. As mentioned in the infographic, the three tracks are explained as follows:

## Phase 1 - Technical setup (IT Administrator) {#phase1technicalsetupitadministrator}

In Track 1, IT Administrator of your organization can switch to Integration Administrator role in Learning Manager application and perform some activation and integrations as follows: 

### Enable/Add Active fields (Learning Manager Administrator) {#enableaddactivefieldscaptivateprimeadministrator}

In addition to the active fields provided by users during registration, the Administrator can add more active fields. Administrator can also enable/disable the user fields. The values for these active fields are generated from the metadata from various data sources associated with user accounts. Refer to [Active Fields Help](feature-summary/add-users-user-groups.md#active-fields) for more information. 

### Single Sign-On (SSO) {#singlesignonsso}

You can access Learning Manager application using Adobe ID or by using Single Sign-On. Single sign‑on is a mechanism that allows a user to authenticate once and gain access to multiple applications many number of times. This configuration is not mandatory for the organization. If your organization has SAML 2.0 based SSO provider, you can use it to configure Learning Manager application. The configuration is required at your organization level and at Learning Manager application. If you choose to use SSO, contact Adobe support to receive configuration instructions. Refer to [Settings Help](feature-summary/settings.md) for more information. 

### Bulk import of users {#bulkimportofusers}

When you have high volume of users in your organization you can import all the users in bulk into Learning Manager application, using a .CSV file. Before doing this task, we suggest you to export the list of users from your organization's HR application in a .CSV format. Even if you do not bulk import the users in at this stage, you can make yourself familiar with the CSV format. To start with the import process in Learning Manager, you upload the .CSV file and map the application data fields with your organization's CSV columns. Refer to [Bulk import Help](add-users-in-bulk.md) for more information. 

### FTP connector integration {#ftpconnectorintegration}

If you face continuous addition or removal of employees in your organization, you can choose to automate the bulk import of users by using FTP connector. You have to establish a connection first, then you can upload a CSV and map the attributes of CSV with corresponding Learning Manager fields. You can schedule the auto import process and also sync it up as and when required. Refer to [FTP connector Help](../integration-admin/feature-summary/connectors.md#ftpconnector) for more information. 

### Salesforce connector integration {#salesforceconnectorintegration}

If you have Salesforce account in your organization, you can automate the process of importing all the users from Salesforce into Learning Manager application. If you want to use this feature, you can use Salesforce connector to integrate Learning Manager with Salesforce account and automate data synchronization. Use auto scheduling feature to perform the automated user import regularly. You can also perform sync on daily basis. Refer to [Salesforce connector Help](../integration-admin/feature-summary/connectors.md#sfconnector) for more information.

### Adobe Connect integration {#adobeconnectintegration}

If you are using Adobe Connect in your organization, you can integrate it with Adobe Learning Manager application to provide seamless user experience to learners. The integration enables your learners to access virtual classrooms right within the Learning Manager application with a single click, without having to log in to Adobe Connect again. Using this feature, your learners can also consume the recorded virtual class room sessions within Learning Manager application. To integrate, integrate the settings first. Use **Settings > Adobe Connect > Configure Now** to provide Connect URL and login credentials and integrate. Refer to [Adobe Connect integration Help](feature-summary/adobeconnect-integration.md) for more information.

### Salesforce app registration {#salesforceappregistration}

Your enterprise learners can have seamless experience of accessing Learning Manager app right within their Salesforce accounts. Learners can access their assigned learning content such as courses, learning programs, and job aids from Salesforce application. Users can also access notifications and announcements from the Learning Manager app within Salesforce. To use this functionality, you have to register the Salesforce featured app in Learning Manager application. Refer to [Salesforce app Help](../integration-admin/feature-summary/sfdc-app.md) to learn about the installation and usage instructions.

## Phase 2 - Site configuration (Learning Manager Administrator) {#phase2siteconfigurationcaptivateprimeadministrator}

Learning Manager application Administrator at your organization has to configure or set-up some of the features before you start implementing them for your learners. 

### Branding {#branding}

An organization may want to display the company logo in Learning Manager application, have its own domain in the URL, display organization name, and display color schemes that match an organization's brand. Learning Manager enables organizations to use all these features. If you want to customize settings and use your own branding, click Branding section at the left pane. Click Edit next to all these options and customize as per your requirements. Refer to [Branding and Themes Help](feature-summary/themes.md) for more information. 

### Add users/user groups {#addusersusergroups}

As learners are the primary users of your learning content, adding users in learning management system is the primary step. Add users to the Learning Manager application and assign roles to them. You can add users in the following ways: 

#### Add users (Internal) {#addusersinternal}

* **As a single user** - Adding single users into Learning Manager application enables you to try out with some of the users before adding them in bulk. Also, this option is useful when you want to add more single users on need basis, after bulk import of users. 
* **Self-registration** - This option allows Administrators to enable their employees to register themselves into Learning Manager. 
* **Bulk import** (using CSV upload) - Using this option you can import users in bulk into Learning Manager application. As a pre-requisite, you have to keep the list of users ready in CSV format before using this feature. 

#### Add users (external profiles) {#addusersexternalprofiles}

* Through external enrollment - Using this option, you can enroll external department members or external employees of your organization to the application.

#### Add user groups {#addusergroups}

Learning Manager application generates default user groups based on similar attributes. In addition to the default groups, you can generate customized user groups based on parameters such as designation, location so that you can utilize those groups in Gamification and reports among others. Refer to [Add users Help](feature-summary/add-users-user-groups.md) for more information.

### Assign roles {#assignroles}

After the users are added to Learning Manager, Administrator can start assigning Author, Administrator or Integration Admin roles to the users as per the organization requirements. To assign roles to users, in the Administrator login, you can click **[!UICONTROL Users]**  on the left pane, select the checkbox against each user name, and click **[!UICONTROL Actions]** drop-down to choose the role you want to assign. Manager roles are assigned to users by Adobe Learning Manager based on the roles/privileges mentioned by your organization in the CSV file. You can also change the roles of users as Managers using the Edit users workflow. Refer to [Add users Help](feature-summary/add-users-user-groups.md) for more information.

### Notification templates {#notificationtemplates}

Notifications can be useful for users in a Learning management system to know their status or to be informed about the events/activities. While creating courses, configuring the features or while consuming courses, users go through several events that trigger notifications to learners, their managers, administrators or authors. Learning Manager provides various email notification templates in the application. As an Administrator, you can customize them as per your organization requirements. To create email notifications, choose **Email Templates** on the left pane and click the template name. Refer to [Email templates Help](feature-summary/email-templates.md) for more information

**Turn off email notifications (recommended)**

By default, the notifications are enabled in Learning Manager application. You can turn off notifications at this stage, if you do not want to notify your employees of the organization. 

### Badges {#badges}

Badges are a measure of achievement that your employee can earn upon completing a course. Professionals across the globe use these badges as a representation of particular skill or a learning achievement. You can create a collection of badges so that you can assign them to learners upon completion of learning content. To start creating badges, you can click **[!UICONTROL Badges]** feature on the left pane. Refer to  [Badges Help](feature-summary/badges.md) for more information. 

### Feedback {#feedback}

Feedback is one of the important factors of an LMS to measure learning progress of learners and to ensure quality in learning content. Learning Manager provides two types of feedback options to users. 

* L1 feedback is the feedback given by learners after completing the course.
* L3 feedback is the feedback given by Managers to learners based on course impact on learners' behavior and day to day activities.

It is optional for organizations to use this feature. Administrators can customize the Feedback templates as per your organization requirements. To use this feature, Administrator has to enable L1 and L3 feedback options at course instance level. To configure the feedback, choose any course, click Instance defaults on the left pane and enable the feedback option. Refer to [Feedback Help](feature-summary/courses.md) for more information.

### Gamification {#gamification}

Keeping learners engaged while they consume the content is one of the challenges faced by organizations. Gamification increases course completion rate by engaging and motivating learners to achieve their goals, with gaming techniques. Learners can compete with their colleagues to score points for various learning activities and achieve bronze, silver, gold, and platinum levels. Administrators can enable/disable each Gamification task and modify allocation of points to tasks. Learning Manager provides the Gamification feature with some default settings. You can start using the feature with default settings for some time and then you may choose to customize. It is optional for you to configure/change the settings for this feature. If you have a subject expert at your organization, then we recommend you to configure the settings before using it. Refer to [Gamification Help](feature-summary/gamification.md) for more information.

### Create learning objects {#createlearningobjects}

This is the logical stage where all the three tracks (track1, track 2, and track 3) converge for you to take up next course of action.

At this point, having created modules and courses, you can start creating higher level learning objects such as certifications, learning programs, or job aids to proceed further. Before you start creating learning objects ensure you have already added some users in the Learning Manager application, created some modules, and courses.

#### Create certifications {#createcertifications}

Certification is a proof of completion of a learning content or a proof of achievement for learners on a one-time basis or on a recurring time frame. Enrollment of learners to learning content can be increased by providing certification to learners after course completion. As an Administrator, you can create a certification program either hosted internally or conducted by a third party. In internal certification, define the courses that a learner has to complete to get certified. Before creating certification, ensure you have some courses available in the account. Refer to  [Certification Help](feature-summary/certifications.md) for more information on how to create certifications.

#### Create Job aids {#createjobaids}

Job aids is a repository of training content that is accessible to learners without any enrollment or completion criteria. Learners can refer to these job aids while they are on the job to get assistance for performing any activity or task in an organization. Even though it is not mandatory to use job aids as part of course creation, Learning Manager team recommends that you create job aids as a best practice for your organization. Refer to the  [Job aids Help](../authors/feature-summary/job-aids.md) for information on how to create job aids.

#### Create learning programs {#createlearningprograms}

Learning programs are a set of uniquely designed courses meeting specific learner goals. Before creating learning programs, ensure you have already created some courses or there are existing courses available in your account.  Even though it is optional for an organization to use this feature, Learning Manager team recommends you to use it to inculcate focused learning for your employees. To start using the learning programs, click Learning programs on the left pane, choose a set of courses from the catalog and publish. Refer to the [Learning programs Help](feature-summary/learning-programs.md) for specific instructions. 

### Create catalogs {#createcatalogs}

You can use catalogs in an organization to create a targeted content or to classify content to defined set of learners. In Learning Manager, a catalog is a collection of learning objects such as courses, certifications or learning programs. You can choose the learning objects of your choice while creating catalogs. Ensure you have already created a set of courses, certifications or learning programs before creating the catalogs. You can custom create catalogs with a set of learning objects if you want to assign them to any internal or external user groups. Refer to the  [Catalogs Help](feature-summary/catalogs.md) for more information on catalogs.

### Turn on email notifications/user access {#turnonemailnotificationsuseraccess}

At this stage, you can turn on email notifications to your applications' users and also enable user access.

## Phase 3 - Authoring courses (Author) {#phase3authoringcoursesauthor}

Content developers or authors in your organization can start creating the learning content. It is mandatory that you create modules and courses as they form the basis for all your learning content in the Learning Manager application. 

### Create modules {#createmodules}

Modules are the basic building blocks of Learning Manager application. To organize your learning content, start creating modules as an Author. Learning Manager allows you to choose any of the four types of course modules, such as classroom, self-paced, Activity, and virtual classroom modules. Refer to  [Modules Help](../authors/how-to-choose-modules.md) to learn about which type of course module is best suited for your organization's needs. 

### Create courses {#createcourses}

Administrators can assume an Author role in Learning Manager application and create courses. In Learning Manager application, a Course is a basic unit with a set of modules, that can be assigned to learner. Learners consume courses. You can start creating courses by choosing the modules you created earlier, associate skills that you want learners to achieve from the course, associate levels, credits and badges to a course, select job-aids, pre-requisites and resources based on your choice and publish the course. You can also create multiple instances of a course so that you can assign the course instances to multiple learners in different time zones, schedule and so on. Refer to the  [Courses Help](../authors/feature-summary/courses.md)for more information on how to create a course.

### Create learning objects {#Createlearningobjects-1}

This is the logical stage where all the three tracks (track1, track 2, and track 3) converge for you to take up next course of action.

At this point, having created modules and courses, you can start creating higher level learning objects such as certifications, learning programs, or job aids to proceed further. Before you start creating learning objects ensure that you have already added some users in the Learning Manager application, created some modules, and courses.

#### Create certifications {#Createcertifications-1}

Certification is a proof of completion of a learning content or a proof of achievement for learners on a one-time basis or on a recurring time frame. Enrollment of learners to learning content can be increased by providing certification to learners after course completion. As an Administrator, you can create a certification program either hosted internally or conducted by a third party. In internal certification, define the courses that a learner has to complete to get certified. Before creating certification, ensure you have some courses available in the account. Refer to  [Certification Help](feature-summary/certifications.md) for more information on how to create certifications.

#### Create Job aids {#CreateJobaids-1}

Job aids is a repository of training content that is accessible to learners without any enrollment or completion criteria. Learners can refer to these job aids while they are on the job to get assistance for performing any activity or task in an organization. Even though it is not mandatory to use job aids as part of course creation, Learning Manager team recommends that you create job aids as a best practice for your organization. Refer to the  [Job aids Help](../authors/feature-summary/job-aids.md) for information on how to create job aids.

#### Create learning programs {#Createlearningprograms-1}

Learning programs are a set of uniquely designed courses meeting specific learner goals. Before creating learning programs, ensure you have already created some courses or there are existing courses available in your account.  Even though it is optional for an organization to use this feature, Learning Manager team recommends you to use it to inculcate focused learning for your employees. To start using the learning programs, click Learning programs on the left pane, choose a set of courses from the catalog and publish. Refer to the [Learning programs Help](feature-summary/learning-programs.md) for specific instructions. 

## Phase 4 - Managing your LMS ( Learning Manager Administrator) {#phase4managingyourlmscaptivateprimeadministrator}

### Announcements {#announcements}

Announcements are useful to the organization to dissipate any important information to all learners of an account at once. In Learning Manager application, an announcement is a multimedia message (text, image or video) that an Administrator can craft and broadcast to a defined set of user groups and learning objects. You can send announcements instantly or schedule them to trigger automatically on a specific date. If you want to use this feature in Learning Manager application, choose Announcements from the left pane and click Add to create announcements. Refer to [Announcements Help](feature-summary/announcements.md) for more information. 

### User enrollment {#userenrollment}

User enrollment is an important step for an LMS application. At this stage, you can start enrolling the learners to various learning objects of Learning Manager application. You can enroll learners either manually or in an automated way, by using learning plans.

#### Manual enrollment {#manualenrollment}

* **Self-Enroll -** If you enable this option while creating a learning object, learners can enroll themselves to the learning objects.
* **Manager Approval** - If you choose this option in enrollment type while creating a course, managers need to approve the learners' enrollment.
* **Manager Nomination** - If you choose this enrollment type during course creation, then such courses have to be nominated by Managers.  
* **Admin Enroll** - In this case, Administrator can enroll some of the learners based on the organization's requirements.

Refer to [User enrollment Help](feature-summary/courses.md)content for more information.

Enroll learners to learning objects manually using the following four ways:

### Automated enrollment {#automatedenrollment}

Automate the learners' enrollment to learning objects, using learning plans. 

#### Learning plans (based on triggers) {#learningplansbasedontriggers}

You can use learning plans to automatically assign courses, learning programs or certifications to learners, based on the occurrence of certain events. For example,

* New user gets added
* User changes user group
* Learner completes a learning object
* User completes a skill

Refer to [Learning plans Help](feature-summary/learning-plans.md)  content for more information.

### Create reports {#createreports}

At this stage, you can start creating and managing various types of reports. 

Adobe Learning Manager enables you to create various reports to track, monitor, and control learner activities. You can use following three types of reporting features to generate reports: 

* **Reports dashboard** - Create summation reports to get actionable insights into your learners' consumption of learning content, based on various categories such as user groups, effectiveness, learners time on courses and so on.  
* **Learner transcripts** - Create learner centric reports with complete history of learners right from the registration day to till date. 
* **Course reports** - Create learners' course consumption statistics from individual courses. You can also create quiz reports at course level. 

Refer to  [Reports Help](feature-summary/reports.md) for more information on report generation process.

For any other information related to Learning Manager application features usage, refer to [Learning Manager Help](../topics.md) based on each role. 
