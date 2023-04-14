# Building a Killer Workspace Experience with UI Builder

## Goal

In this lab you will learn how to use UI Builder to build and configure a workspace for a custom application. You will start with a prebuilt application to manage a company's fleet of vehicles.

You will use UI Builder to open a starter workspace experience created from App Engine Studio to build out the fulfiller workspace experience to make it easier to interact with the application and make your fulfillers more productive. This lab will touch on a number of different parts of UI Builder while you create the custom experience including but not limited to:

* Creating lists
* Creating new pages
* Page parameters
* Data resources
* Client state parameters
* Client scripts
* Configuring components
* Using the repeater component
* Updating ServiceNow records from the experience
* Working with the Standard Record Page template

## Lab Objective

The primary objective of this lab is to expose you to the different parts of configuring and customizing a workspace. A very basic fleet vehicle management workspace exists in your instance and you will configure it similarly to how you would configure one of ServiceNow's default workspaces.

## (Optional) Pre-flight check

If you're doing this lab during CreatorCon, you'll be working on an instance on NowLearning loaded with the FLeet Vehicle Management application. If you're following along with this lab guide on a Personal Developer Instance (PDI), please follow the instructions in the Appendix at the end of this lab guide to learn how to pull in the Fleet Vehicle Management application.

# Exercise 1 - Basic Workspace Configuration

## Explore the base version of the app

1. In your instance, go to **Workspaces \> Fleet Vehicle Management**.

    You'll notice that the homepage is very generic and doesn't really fit our requirements, so you'll be adding a new variant and customizing that. 

1. Click on the list icon in the L1 menu on the left.

    ![](images/2023-04-14-09-43-02.png)

    Notice that the lists that come up on the left could be organized better, which we'll do.

1. Click into one of the requests.

    You'll notice the form that comes up just has the two tabs so we'll be enhancing that as well.

## Open the app in UI Builder

1. In the top menu in your instance, click **All**, type *App Engine* into the filter, and click **App Engine Studio** to launch *App Engine Studio*, or *AES* as we'll call it moving forward.

  The app currently consists of the following primary tables:

     * Vehicle
     * Maintenance requests
     * Maintenance tasks
     * Parts

1. Open UI Builder by clicking on the **Fleet Vehicle Management** workspace under *Experiences*.

  ![](images/2023-03-17-10-23-19.png)

  This will open the experience in UI Builder's experience view.

## Consolidate lists

In this section you'll do some consolidating of the lists in the workspace.

1. In the experience view choose the **List default** variant to open the list page in UIB.

1. Click on the **List nav** component to select it.

1. You'll see the config panel on the right side of your UIB page. Choose **Configuration** at the bottom. This will open the UX List Menu COnfigurations in a new tab. 
   
2. Choose **Fleet Vehicle Management_menu_config** to open the list configuration for this workspace experience.

3. In the related lists you'll see the 7 default menu categories and the 13 default lists. 

1. Use the **New** button to create a new UX List Category.

1. Give it the following values and choose **Submit**:

    * Title: Administration
    * Order: 1000

2. Click into **Maint req**, edit the following, and click **Update**:

    * Name: Maintenance Requests

2. Click into **Maint task**, edit the following, and click **Update**:

    * Name: Maintenance Tasks
    * Order: 200

1. Click into the **UX Lists** tab.

1. Use list editing to change the *Category* of each of the following UX Lists to **Administration** and the titles to match their table names:

    * Parts
    * Vehicles
    * Part reference
    * Manufacturers
    * Models

    ![](images/2023-04-14-10-02-19.png)

1. Now go back to the list view for the workspace from the previous exercise and do a refresh. You should see the new list structure.

## Configure the form

<!--The activity stream component shows up when you add the formatter to the form. Add the formatter, work notes, and comments to the form and see what happens. Then add the email client.-->

Now you'll do some form configuration. Since there is only one form view for our maint req table we don't have to worry about which form view we're using. If you're confgiuring the incident table or another table with multiple views you'll need to make sure you're editing the view that's being shown in the workspace. This generally set in the UX Page Properties for the experience, but could work differently in different workspaces.

1. If you still have the list page open, use the dropdown at the top to switch to the **Record page**.

<!-- update the page in the base app so it shows a maintenance request -->

1. Click **Open** at the top right to open the page in runtime in a new tab for testing. You'll see that it's missing the activity stream component and email functionality. Let's add it.

1. Back in your UI Builder tab, find and click on the **form** component.

    <!-- Insert screenshot -->

1. In the config panel on the right, click **Edit form view** to open table builder in a new tab.

1. At the top left, click **More** and choose **Formatters**.

    <!-- Insert screenshot -->

1. Add the **Avitivities (filtered)** formatter at the bottom of the form and choose **Save**.

1. Go back to the browser tab where the rendered record page is showing and hit refresh. You'll see that the activity stream now shows up on the right.

    > Note that there is a check on the workspace side of things that checks to see if the activity formatter is present and then shows the acitivty stream component if so. It doesn't matter where you add the activity formatter in table builder, it will always show in the same place on the UIB page unless you edit the UIB page and move it.

1. Notice that only work notes is accessible in the page. Go back to the table builder and add the additional comments field above the activities formatter.

1. Click save and refresh the rendered tab. You should now see the ability to post comments or work notes.

1. Now let's add email capabilities to the form. In table builder click **Preview**.

  <!-- Insert screenshot -->

1. In the view that comes up click **Open form in Platform** at the very top right.

  <!-- Insert screenshot -->

1. Right lick on the form header and choose **Configure > Dictionary**.

  <!-- Insert screenshot -->

1. Choose the dictionary entry without a column name where Type is Collection.

1. Click **Advanced view** under Related Links.

1. In the Attributes field add **email_client=true** and choose **Update** to save your changes.

1. In your rendered form tab refresh and choose the horizontal three dots menu to the right of the **Save** button. You should now see a *Compose Email* option.

# Exercise 2 - Enhance the experience home page

High mileage vehicles

Vehicle typeahead search

# Exercise 3 - Enhance the Record Page for Vehicles

## Create a variant for Vehicles

## Edit secondary items in header

## Add an overview tab to the variant

# Add contextual sidebar content

# Exercise 4 - Create actions and buttons

## Add a close task button

Create a UI Action and associate it with the table

## Open a new request from the overview tab

# Exercise 5 - Miscellaneous

## Do something with UX Page Properties to show how they work

## Record watcher

## User experience analytics

# Challenge Exercise