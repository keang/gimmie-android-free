#Gimmie on Android Quickstart Guide

Integrating with new project
----------------------------------

- Import the downloaded Gimmie-library as "existing android project"
- Add the Gimmie-library project as a library reference in your project
- Add the following Manifest delcarations inside the ````<application>```` tag:
    ````xml
        <!-- Gimmie declarations -->
        <activity
            android:name="com.gimmie.components.GimmieView"
            android:theme="@style/RewardCategoryPage" >
        </activity>
        <activity
            android:name="com.gimmie.components.RewardDetail"
            android:theme="@style/GimmieAppeaerance" />
        <activity
            android:name="com.gimmie.components.BadgeView"
            android:theme="@style/GimmieAppeaerance" />
        <activity
            android:name="com.gimmie.components.ClaimsList"
            android:theme="@style/GimmieAppeaerance" />
        <activity
            android:name="com.gimmie.components.HistoryList"
            android:theme="@style/GimmieAppeaerance" />
        <activity
            android:name="com.gimmie.components.WebView"
            android:theme="@style/GimmieAppeaerance" />

        <meta-data
            android:name="com.gimmie.notification.popup.enable"
            android:value="true" />
        <meta-data
            android:name="com.gimmie.notification.popup.duration"
            android:value="10" />

        <!-- end of Gimmie Declarations -->
    ````

- Add permissions for your project, outside the ````<application>```` tag:
    ````xml
        <uses-permission android:name="android.permission.INTERNET"/>
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
        <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
            <!-- for push notification -->
    	<uses-permission android:name="android.permission.GET_ACCOUNTS" />
    	<uses-permission android:name="android.permission.GET_TASKS"/>
    	<uses-permission android:name="android.permission.WAKE_LOCK" />
    	<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    	<permission android:name="com.gimmie.demo.permission.C2D_MESSAGE"
	        android:protectionLevel="signature" />
	    <uses-permission android:name="com.kakada.gcmtest.permission.C2D_MESSAGE" />
    ````

Initialize
---------------------
- Add the following to initialize the shared version of Gimmie, in onCreate() of your activity:
    ````
        Gimmie.initializeSharedGimmie(this);
    ````
- Add the following to instruct Gimmie to show notifications in the correct context:
    ````
    	GimmieComponents.setNotificationContext(this); //'this' is the activity
    ```

Call Gimmie
-----------------------
- Show Rewards Catalog with the following:
```
        Gimmie.getInstance().getGimmieComponents().showRewardsCatalogue();
````
