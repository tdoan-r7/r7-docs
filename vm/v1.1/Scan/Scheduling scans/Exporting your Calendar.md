---
title: "Exporting your Calendar"
excerpt: ""
---
Your InsightVM calendar can help you stay up to date with all your scheduled scans and reports. By using an external calendar, you can easily track your schedule events without logging in to your security console. To help you view your calendar outside of the security console, you can export it and import it into an external calendar, such as Outlook or iCal.

There are two options for exporting your InsightVM calendar:

* You can download an ICS file and import it into your external calendar.
* You can subscribe to your calendar by adding an ICS URL to your external calendar.

## Downloading and importing an ICS file

An ICS file contains a static snapshot of your calendar. Any changes that you make to your InsightVM calendar will not be automatically updated in your external calendar. To keep the calendar up to date, you should subscribe to your InsightVM calendar. Otherwise, the only way to refresh your external calendar will be to import a more current snapshot.

**To download and import an ICS file:**

1. Select **Administration** from the left navigation menu.
2. Under the _Calendar_ options, click the **View** link for the monthly calendar of scheduled scans and reports. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a8c3ad4-s_nx_calendar_view.jpg",
        "s_nx_calendar_view.jpg",
        1326,
        293,
        "#eaeff1"
      ]
    }
  ]
}
[/block]
3. Click the **Export** button. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4334316-s_nx_calendar.JPG",
        "s_nx_calendar.JPG",
        1228,
        571,
        "#dff1f3"
      ]
    }
  ]
}
[/block]
4. When the _Calendar Export_ window appears, select the **Download ICS file** option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c5c076c-s_nx_calendar_download_ics_file_option.jpg",
        "s_nx_calendar_download_ics_file_option.jpg",
        600,
        342,
        "#e9eff0"
      ]
    }
  ]
}
[/block]
5. Click the **Download** button. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/35c23e7-s_nx_calendar_download_ics_file_button.jpg",
        "s_nx_calendar_download_ics_file_button.jpg",
        600,
        342,
        "#e9eff0"
      ]
    }
  ]
}
[/block]
6. Save the ICS file to your computer.
7. In your external calendar, import the ICS file. For more information on importing ICS files, please check the documentation that is available for your external calendar. 

For Outlook, you can visit [https://support.office.com/en-us/article/Import-iCal-or-Address-Book-items-into-Outlook-2a637ac6-f3b5-411d-8a73-016bd90c1094](https://support.office.com/en-us/article/Import-iCal-or-Address-Book-items-into-Outlook-2a637ac6-f3b5-411d-8a73-016bd90c1094). 

For iCal, you can visit [https://support.apple.com/kb/PH11524?locale=en_US](https://support.apple.com/kb/PH11524?locale=en_US).

## Subscribing to your calendar

A subscription enables you to share the details of your InsightVM calendar with an external calendar, such as Outlook or iCal. Any changes that are made to the InsightVM calendar will automatically appear on your external calendar.

In order to subscribe to your InsightVMcalendar, you'll need to generate an ICS URL and add it to your external calendar. The ICS URL contains the details that are required for your InsightVM calendar to be viewed in an external calendar. To protect your data, the details that are exposed are minimal, but it does contain sufficient information to recreate a calendar of your scan schedules. Your scan schedule details will not be made available unless you generate an ICS URL.

Anyone who has access to the ICS URL will be able to access your scan schedule details, such as your scan times and site names. To help prevent unauthorized access to your calendar's details, the generated URL will contain a unique sequence of numbers and letters that will make it difficult for it to be bruteforced. These security measures will help protect your scan schedule details from being gained by or used for malicious purposes.

By generating this URL, you agree that your scan details are available and accessible to anyone who has access to the URL. Because of this, it is critical that you only share the URL with trusted individuals.

**To subscribe to your calendar:**

1. Select **Administration** from the left navigation menu.
2. Under the _Calendar_ options, click the **View** link for the monthly calendar of scheduled scans and reports. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b8e79ba-s_nx_calendar_view.jpg",
        "s_nx_calendar_view.jpg",
        1326,
        293,
        "#eaeff1"
      ]
    }
  ]
}
[/block]
3. Click the **Export** button.
4. When the _Calendar Export_ window appears, select the **Subscribe to your calendar** option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c612ce3-s_nx_calendar_subscribe_option.jpg",
        "s_nx_calendar_subscribe_option.jpg",
        598,
        337,
        "#eaf1f1"
      ]
    }
  ]
}
[/block]
5. Click the Generate ICS URL button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9322420-s_nx_calendar_generate_ics_url_button.jpg",
        "s_nx_calendar_generate_ics_url_button.jpg",
        598,
        337,
        "#eaf1f1"
      ]
    }
  ]
}
[/block]
6. When the ICS URL displays, copy it. You'll need it for your external calendar. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/69e01fe-s_nx_calendar_ics_url.jpg",
        "s_nx_calendar_ics_url.jpg",
        599,
        337,
        "#eaf0f1"
      ]
    }
  ]
}
[/block]
7. In your external calendar, add the ICS URL. For more information on adding an ICS URL, please check the documentation that is available for your external calendar. 

For Outlook, you can visit [http://windows.microsoft.com/en-us/windows/outlook/calendar-import-vs-subscribe](http://windows.microsoft.com/en-us/windows/outlook/calendar-import-vs-subscribe). 

For iCal, you can visit [https://support.apple.com/en-us/HT201747](https://support.apple.com/en-us/HT201747).

### Canceling a subscription

To disable the ICS URL, you can cancel the subscription. InsightVM will no longer update the events in your external calendar.

**To subscribe to your calendar:**

1. Select **Administration** from the left navigation menu.
2. Under the _Calendar_ options, click the **View** link for the monthly calendar of scheduled scans and reports.
3. Click the **Export** button.
4. When the _Calendar Export_ window appears, select the **Subscribe to your calendar** option. 
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7856f87-s_nx_calendar_subscribe_option.jpg",
        "s_nx_calendar_subscribe_option.jpg",
        598,
        337,
        "#eaf1f1"
      ]
    }
  ]
}
[/block]
5. Click the **Cancel Subscription** button.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b5d280f-s_nx_calendar_cancel_subscription.jpg",
        "s_nx_calendar_cancel_subscription.jpg",
        599,
        337,
        "#eaf0f1"
      ]
    }
  ]
}
[/block]
## Enabling universal compatibility for external calendars

InsightVM outputs ICS files using Coordinated Universal (UTC) time to support universal compatibility. After you import an ICS file or subscribe to an ICS URL, you will need to disable daylight savings to ensure that your external calendar accurately matches your InsightVM calendar.

To learn more about how you can modify your calendar's timezones, you can read the following resources:

iCal — [https://support.apple.com/kb/PH2677](https://support.apple.com/kb/PH2677)
Outlook — [https://support.office.com/en-us/article/Add-remove-or-change-time-zones-8dc68954-a111-43c3-b51d-f5ccfddc08d6#bm3](https://support.office.com/en-us/article/Add-remove-or-change-time-zones-8dc68954-a111-43c3-b51d-f5ccfddc08d6#bm3)