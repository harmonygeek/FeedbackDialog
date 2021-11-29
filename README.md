[![Build](https://github.com/applibgroup/FeedbackDialog/actions/workflows/main.yml/badge.svg)](https://github.com/applibgroup/FeedbackDialog/actions/workflows/main.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=applibgroup_FeedbackDialog&metric=alert_status)](https://sonarcloud.io/project/configuration?id=applibgroup_FeedbackDialog)
[![license](https://img.shields.io/github/license/applibgroup/FeedbackDialog?color=blue)](LICENSE)
![1.0.0](https://img.shields.io/badge/version-1.0.0-blue.svg)

# FeedbackDialog

An Interactive Feedback Dialog for HMOS inspired from Google Maps Review section

Getting feedback from your customers, prospects is the most important task for developing and moving a product. Getting inspired from Google Maps Review section, I've compiled and crafted this library to make sure this utility will be helpful to get feedback from customers easily without any monotonous forms fillup and with less input.

## Screenshots

Here are the screenshot showing the functionality you get with this library:

|<img src="/screenshots/screenshot1.png?raw=true" width="400" >| <img src="/screenshots/screenshot2.png?raw=true" width="400" > 
|--|--|
| <img src="/screenshots/screenshot3.png?raw=true" width="400" >| <img src="/screenshots/screenshot4.png?raw=true" width="400" >|

## Source

Inspired from android library <https://github.com/shivasurya/FeedbackDialog>.

## Integration

1.For using FeedbackDialog module in sample app, include the source code and add the below dependencies in entry/build.gradle to generate hap/FeedbackDialog.har.

```
   dependencies {
       implementation project(':FeedbackDialog')
   }
```

2.For using FeedbackDialog in separate application using har file, add the har file in the entry/libs folder and add the dependencies in entry/build.gradle file.

```
   dependencies {
      implementation fileTree(dir: 'libs', include: ['*.har'])     
   }
```

## Usage

As simple as AlertDialog API,
```java
FeedBackDialog mDialog = new FeedBackDialog(MainAbilitySlice.this)
    .setBackgroundColor(ResourceTable.Color_sampleColor)
    .setIcon(ResourceTable.Media_reviewdialog_ic_restaurant)
    .setIconColor(ResourceTable.Color_sampleColor)
    .setTitle(ResourceTable.String_brand_name)
    .setDescription(ResourceTable.String_brand_description)
    .setReviewQuestion(ResourceTable.String_customer_review_questions)
    .setPositiveFeedbackText(ResourceTable.String_positive_feedback_text)
    .setPositiveFeedbackIcon(ResourceTable.Media_reviewdialog_ic_accept_action)
    .setNegativeFeedbackText(ResourceTable.String_negative_feedback_text)
    .setNegativeFeedbackIcon(ResourceTable.Media_reviewdialog_ic_cancel_action)
    .setAmbiguityFeedbackText(ResourceTable.String_ambiguity_feedback_text)
    .setAmbiguityFeedbackIcon(ResourceTable.Media_reviewdialog_ic_ambiguity_action)
    .setOnReviewClickListener(new FeedBackActionsListeners() {
        @Override
        public void onPositiveFeedback(FeedBackDialog dialog) {
            dialog.dismiss();
        }

        @Override
        public void onNegativeFeedback(FeedBackDialog dialog) {
            dialog.dismiss();
        }

        @Override
        public void onAmbiguityFeedback(FeedBackDialog dialog) {
            dialog.dismiss();
        }

        @Override
        public void onCancelListener(IDialog dialog) {
            dialog.destroy();
        }
    })
    .show(); // Finally don't forget to call show()                
``` 

## Feedback Dialog API   

You can check below some of the exposed API methods to control the Dialog appearance and actions.                

1. ```setIcon(int mIcon)``` - set Media Image at top of the Dialog as Icon. <br />
2. ```setTitle(int mTitle)``` -  set Title or Brand Name for the Feedback Dialog
3. ```setDescription(int mDescription)``` - set Description or Additional text for Feedback Dialog
4. ```setPositiveFeedbackText(int mPositiveFeedbackText)``` - set Positive Feedback button text
5. ```setNegativeFeedbackText(int mNegativeFeedbackText)``` - set Negative Feedback button text
6. ```setAmbiguityFeedbackText(int mAmbiguityFeedbackText``` - set Ambiguity Feedback button text
7. ```setPositiveFeedbackIcon(int mPositiveFeedbackIcon)``` - set Positive Feedback button Icon as element resource
8. ```setNegativeFeedbackIcon(int mNegativeFeedbackIcon)``` - set Negative Feedback button Icon as element resource
9. ```setAmbiguityFeedbackIcon(int mAmbiguityFeedbackIcon)``` - set Ambiguity Feedback button Icon as element resource
10. ```setBackgroundColor(int mBackgroundColor)``` - set Feedback Dialog background color
11. ```setIconColor(int mIconColor)``` - set Title and Action Icon colors
12. ```setReviewQuestion(int mReviewQuestion)``` - set Questionable message to end-user which is shown in Dialog
13. ```setOnReviewClickListener(FeedBackActionsListeners reviewActionsListeners)``` - set Feedback Action listeners which implements action listeners callback.
14. ```destroy()``` - destroy the active Feedback Dialog
    
## License

```
Copyright 2015 the original author or authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.    
```