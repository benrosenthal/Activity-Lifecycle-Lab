
---

| Title | Type | Duration | Name | City |
| --- | --- | --- | --- | --- |
| Activity Lifecycle | Lab | "1:00" | James Davis | NYC |

---  
# Activity Lifecycle Lab

## Introduction

Below, you will find three scenarios, and questions following each one.

To the best of your ability, answer the questions **in english**, not in code.

Below the scenarios, you will find a few questions. Answer those however you'd like.

Answer the questions by editing this readme, pushing your changes to your forked repo, and making a pull request.

## Exercise  


####Scenario 1:

Let’s say you made a To Do list app, where you can add things to a list and cross them off. You decide to cross some items off the list and mark them as complete.

When you rotate the device, the things you marked as complete are no longer crossed off.

**Question**: Why did this happen?
<br />Answer: MainActivity is released from memory and must be recreated to be used again. Any changes were not saved due to the execution of the Activity's onDestroy method. 

**Question**: How do you fix this issue?
<br />Answer: Save any changes to the data in the onSaveInstanceState method, and retrieve it in onCreate. 


####Scenario 2:

The Amazon Kindle Android app allows you to open and read eBooks. You discovered a bug! You opened a book, and read it from the beginning up to page 68. Then, you left the app and closed it completely so you can do other things.

When you opened the app again, and opened the book, it started from page 1 (and not page 68 where you left off)!

**Question**: How would you fix this issue?
<br />**Answer**: An incremented int variable that's incremented each time a turnPage method is called is passed to onPause in the onClickListener for the system's back button in which a sharedPreferences object is instantiated. The int pageNumber variable would be put/edited to the sharedPreferences object. The page # value would be retrieved from an instantiated sharedPreferences in onResume. 


####Scenario 3:

Facebook for Android added a feature last year where, if you started writing a comment on someone’s post and decided not to do so, the app would save a draft of it just in case you changed your mind.

Take this scenario. On a post on Facebook, you click the “comment” button (which opens a new CommentActivity). You start writing a comment, and then change your mind by pressing the back key (which closes the CommentActivity). You click on the “comment” button again, and in the newly-opened CommentActivity, the comment you were writing is still there.

**Question**: How would you implement this feature? Be specific; what lifecycle methods would you use in CommentActivity, and what techniques would you use?
<br />**Answer**:To save additional state information for your activity, one option is to implement onSaveInstanceState() and add key-value pairs to a Bundle object. Instead of restoring the state during onCreate(), implement onRestoreInstanceState(), which the system calls after the onStart() method. When your activity is recreated after it was previously destroyed, you can recover your saved state from the Bundle that the system passes your activity. Both the onCreate() and onRestoreInstanceState() callback methods receive the same Bundle that contains the instance state information. The system calls onRestoreInstanceState() only if there is a saved state to restore, so you do not need to check whether the Bundle is null. 



In your own words…
==================

**Question**: What are the methods of the Activity Lifecycle?
<br />**Answer**: onCreate, onStart, onResume, onPause, onStop, onDestroy

**Question**: What order are the methods called?
<br />**Answer**: onCreate, onStart, onResume, onPause, onStop, onDestroy

**Question**: What is a bundle?
<br />**Answer**: A Bundle object is actually a hash control that stores key and value pairs, typically used to pass data between activities in Intent objects. 

**Question**: How do you get the Shared Preferences of an app?
<br />**Answer**: Shared preferneces is a method that used to persist app settings and other data outside of instance state, or in other words after onDestroy is called. 
After writing the following code block: SharedPreferences sharedPreferences = getPreferences(Context.MODE_PRIVATE);
        SharedPreferences.Editor editor = sharedPreferences.edit();
        editor.putString("timestarted", mTimeStarted);
        editor.commit();
        
We can retrieve the data by: 
SharedPreferences sharedPreferences = getPreferences(Context.MODE_PRIVATE);
Var = savedInstanceState.getString("Key");
        

