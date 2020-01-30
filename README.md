# OneSignalNotification

# Tutorial
Spencer Carli
https://medium.com/differential/react-native-push-notifications-with-onesignal-9db6a7d75e1e

# Install OneSignal
npm install react-native-onesignal --save

# Link package
react-native link react-native-onesignal

# Configure Android
at android/app/src/main/AndroidManifest.xml

    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
        package="com.onesignalexample"
        android:versionCode="1"
        android:versionName="1.0">

        ...
        <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/> <!-- ADD THIS -->
        <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/> <!-- ADD THIS -->

        <uses-sdk
            android:minSdkVersion="16"
            android:targetSdkVersion="22" />

        <application
          ...
        >
            <activity
              ...
              android:launchMode="singleTop" <!-- ADD THIS -->
            >
              ...
            </activity>
          ...
        </application>

    </manifest>

at android/app/build.gradle 

    android {
        ...
        defaultConfig {
            ...
           manifestPlaceholders = [onesignal_app_id: "YOUR_ONESIGNAL_ID",  // Change one_signal_app_id_here
                                    onesignal_google_project_number: "REMOTE"]
        }
    }

App.js

    import React, { Component } from 'react';
    import {
      StyleSheet,
      Text,
      View,
      Platform,
    } from 'react-native';

    class App extends Component {
      render() {
        return (
          <View style={styles.container}>
            <Text style={styles.welcome}>
              Welcome to the OneSignal Example!
            </Text>
            <Text style={styles.instructions}>
              Using {Platform.OS}? Cool.
            </Text>
          </View>
        );
      }
    }

    const styles = StyleSheet.create({
      container: {
        flex: 1,
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#F5FCFF',
      },
      welcome: {
        fontSize: 20,
        textAlign: 'center',
        margin: 10,
      },
      instructions: {
        textAlign: 'center',
        color: '#333333',
        marginBottom: 5,
      },
    });

    export default App;
