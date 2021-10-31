## Lifecycle of a task and its back stack

The device Home screen is the starting place for most tasks. When a user touches the icon for an app or shortcut in the app launcher (or on the Home screen), that app's task comes to the foreground. If no task exists for the app (the app has not been used recently), then a new task is created and the main activity for that app opens as the root activity in the stack.

When the current activity starts another, the new activity is pushed on the top of the stack and takes focus. The previous activity remains in the stack, but is stopped. When an activity stops, the system retains the current state of its user interface. When the user performs the back action, the current activity is popped from the top of the stack (the activity is destroyed) and the previous activity resumes (the previous state of its UI is restored). Activities in the stack are never rearranged, only pushed and popped from the stack—pushed onto the stack when started by the current activity and popped off when the user leaves it using the Back button or gesture. As such, the back stack operates as a last in, first out object structure.

## Back press behavior for root launcher activities
Root launcher activities are activities that declare an Intent filter with both ACTION_MAIN and CATEGORY_LAUNCHER. These activities are unique because they act as entry points into your app from the app launcher and are used to start a task.

When a user presses or gestures Back from a root launcher activity, the system handles the event differently depending on the version of Android that the device is running.

System behavior on Android 11 and lower
The system finishes the activity.
System behavior on Android 12 and higher
The system moves the activity and its task to the background instead of finishing the activity. This behavior matches the default system behavior when navigating out of an app using the Home button or gesture.

In most cases, this behavior means that users can more quickly resume your app from a warm state, instead of having to completely restart the app from a cold state.

If you need to provide custom back navigation, we recommend using the AndroidX Activity APIs, rather than overriding onBackPressed(). The AndroidX Activity APIs automatically defer to the appropriate system behavior if there are no components intercepting the system Back press.

However, if your app overrides onBackPressed() to handle Back navigation and finish the activity, update your implementation to call through to super.onBackPressed() instead of finishing. Calling super.onBackPressed() moves the activity and its task to the background when appropriate and provides a more consistent navigation experience for users across apps.

## Manage tasks
The way Android manages tasks and the back stack, as described above—by placing all activities started in succession in the same task and in a last in, first out stack—works great for most apps and you shouldn't have to worry about how your activities are associated with tasks or how they exist in the back stack. 


## Handle affinities
An affinity indicates which task an activity prefers to belong to. By default, all the activities from the same app have an affinity for each other. So, by default, all activities in the same app prefer to be in the same task. However, you can modify the default affinity for an activity. Activities defined in different apps can share an affinity, or activities defined in the same app can be assigned different task affinities.

## Clear the back stack
If the user leaves a task for a long time, the system clears the task of all activities except the root activity. When the user returns to the task again, only the root activity is restored. The system behaves this way, because, after an extended amount of time, users likely have abandoned what they were doing before and are returning to the task to begin something new.