Edit (james), I've included [an export](./GTM-TTKZ4R_v23.json) from gtm of the tags.

To build this example:

  1. Open CuteAnimals.xcodeproj in XCode.
  2. Select the desired platform from the scheme in the toolbar (or from the
     menu "Product->Destination").
  3. Run the sample by clicking "Run" in the toolbar (or selecting "Product/Run"
     from the menu).

Edit (james), I've included [an export](./GTM-TTKZ4R_v23.json) from gtm of the tags.

This sample uses a container ID for a non-existent container: "GTM-XXXX".
There are two corresponding files: "GTM-XXXX" and "GTM-XXXX.plist" which
are used as default containers.

GTM-XXXX.plist contains default key-value pairs. It is limited to representing
the key-value pairs representable in value collection macros and is ignored if
a GTM-XXXX container is present.

GTM-XXXX is a full-featured default container. It contains the same default
key-value pairs as GTM-XXXX.plist plus the configuration of how to trigger
Universal Analytics tags and a custom function call tag. Here is a summary of
the container (more details can be seen in the snapshot at Images/Container.png)
   8 Macros:
      * "app name": the pre-populated application name macro.
      * "app version": the pre-populated app version macro.
      * "Cute Animals IOS": a value collection macro containing key/value pairs
        as GTM-XXXX.plist.
      * "event": an event macro.
      * "numRefreshes": a custom function call macro which records how many
        times the "Refresh" button is clicked.
      * "numRefreshesMod5": a custom function call macro whose value is equal
        to "numRefreshes" mod 5. See images/NumRefreshesMod5.png for more
        details.
      * "screen name": a data layer macro whose data layer variable name
        is "screenName".
      * "true": the pre-populated constant string macro whose value is equal to
        "true".
   5 Rules:
      * "CustomTagFires": the value of the event macro is equal to 'custom_tag'.
      * "CloseScreenEvent": the value of the event macro is equal to
        'closeScreen'.
      * "OpenScreenEvent": the value of the event macro is equal to
        'openScreen'.
      * "RefreshEvent": the value of the event macro is equal to 'refresh' and
        the value of the numRefreshesMod5 macro is equal to 1. See
        images/RefreshEvent.png for more details.
      * "Always": the pre-populated rule which is always evaluated to true.
   4 Tags:
      * "CustomTag": a custom function call tag with the firing rule:
        CustomTagFires is true. See images/CustomTag.png for more details.
      * "RefreshEvent": a Universal Analytics tag with the firing rule:
        RefreshEvent is true. See Images/RefreshEventTag.png for more details.
      * "ScreenClosed": a Universal Analytics tag with the firing rule:
        CloseScreenEvent is true. See Images/ScreenClosedTag.png for more
        details.
      * "ScreenOpen": a Universal Analytics tag with the firing rule:
        OpenScreenEvent is true. See Images/ScreenOpenTag.png for more
        details.

Although the app will run and use the values specified in the GTM-XXXX (or
GTM-XXXX.plist if you delete GTM-XXXX from your local machine), there's
no way to dynamically update those values, since this is a non-existent
container.

To use real values, create a container in the Tag Manager UI and note the
resulting container ID:

  1. Download the container from the Tag Manager UI and rename it to
     GTM-1234 (where GTM-1234 is the container ID for the new container).
     Put GTM-1234 into the same directory with GTM-XXXX.plist file.
  2. In AppDelegate.m, update the parameter for openContainerById with the
     new container ID.
  3. Optional: delete GTM-XXXX and GTM-XXXX.plist files.

