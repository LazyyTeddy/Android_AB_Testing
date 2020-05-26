# Simple_AB_Testing

( Using Firebase )
A/B testing helps you test improvements to your app on a subset of your users so you can use data to choose the best solution for your entire user base.


## Getting Started

Determine the feature or content variants you want to test.

Set up the features or content to be shown in each test variant and to those users not under test, for example : 

Scenario: New implementation of existing feature

Example: Using Floating Action Button instead of Search Button to increase user engagement.

[Sample Doc.](https://firebase.google.com/docs/ab-testing/?gclid=CjwKCAjw_LL2BRAkEiwAv2Y3SV8jB3ZuE8Mlc616wdEueHR_Fe6D8-hnO4kd8xJdCT1WepaA7z00vhoCzjkQAvD_BwE) how it works.

```bash
FirebaseRemoteConfig firebaseRemoteConfig = FirebaseRemoteConfig.getInstance();

        FirebaseRemoteConfigSettings config = new FirebaseRemoteConfigSettings.Builder()
                .setDeveloperModeEnabled(BuildConfig.DEBUG)
                .build();
        firebaseRemoteConfig.setConfigSettings(config);

        firebaseRemoteConfig.setDefaults(R.xml.remote_config_defaults);

        firebaseRemoteConfig.fetch(0).addOnCompleteListener(new OnCompleteListener<Void>() {
            @Override
            public void onComplete(@NonNull Task<Void> task) {
                if (task.isSuccessful()) {
                    Log.d("TAG", "Fetch Succeeded");
                    firebaseRemoteConfig.activateFetched();
                } else {
                    Log.d("TAG", "Fetch Failed");
                }

            }
        });
```

## Create Firebase Remote Config Experiments with A/B Testing

```python
To A/B test feature variants with a control group, do the following:

Create your experiment.
Validate your experiment on a test device.
Manage your experiment.
```

## Roll out an experiment to all users

After an experiment has run long enough that you have a "leader," or winning variant, for your goal metric, you can roll out the experiment to 100% of users. This allows you to select a value to publish in Remote Config for all users moving forward. Even if your experiment has not created a clear winner, you can still choose to roll out a variant to all of your users.

On the Firebase console navigation bar, click Grow, then click A/B Testing.

Click Completed or Running, click an experiment that you want to roll out to all users, click the context menu (more_vert), and then click Roll out variant.

Roll out your experiment to all users by doing one of the following:

For an experiment that uses the Notifications composer, use the Roll out message dialog to send the message to the remaining targeted users who were not part of the experiment.

For a Remote Config experiment, use the dialog to determine which Remote Config parameter values to change for all users.
