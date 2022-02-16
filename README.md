![logo](./logotype.png)

Android Color Picker
====================

aka `ColorPickerPreference` library ("Color Picker Preference")

This is a small library for your application to enable the users to select an arbitrary color.

If your application has a feature to customize the color of some background, text, or maybe for a painting application where the user can select different colors for painting or filling, then `ColorPickerPreference` is suitable for you.


Adding it to your project
===========

Android Studio 3.0 and above:

```groovy
dependencies {
    implementation 'com.github.DevelopMastr:ColorPickerPreference:1.0.0'
}
```




How to use the dialog
=====================

Create a color picker dialog by calling the following constructor, and then show it.

    PickerDialog(Context context, int color, OnPickerListener listener)

Alpha is also supported by passing the 3rd parameter `supportsAlpha`:

    PickerDialog(Context context, int color, boolean supportsAlpha, OnPickerListener listener)

Example:

    // initialColor is the initially-selected color to be shown in the rectangle on the left of the arrow.
    // for example, 0xff000000 is black, 0xff0000ff is blue. Please be aware of the initial 0xff which is the alpha.
    PickerDialog dialog = new PickerDialog(this, initialColor, new OnPickerListener() {
    	@Override
    	public void onOk(PickerDialog dialog, int color) {
    		// color is the color selected by the user.
    	}
    		
    	@Override
    	public void onCancel(PickerDialog dialog) {
    		// cancel was selected by the user
    	}

    dialog.show();

How to use it as a Preference
=============================


Very simple. It works like a `DialogPreference` that stores an Integer to the shared preferences file.

Just add the following to the preferences xml file.

  	<com.dm.ColorPickerPreference.widget.PickerPreference
  		android:key="your_preference_key"
  		android:defaultValue="0xff6699cc" 
  		android:title="Pick a color" />

To enable alpha, use the application attribute `supportsAlpha`, as follows:

    <PreferenceScreen
    	xmlns:android="http://schemas.android.com/apk/res/android"
    	xmlns:app="http://schemas.android.com/apk/res-auto">
    	
    	<com.dm.ColorPickerPreference.widget.PickerPreference
    		android:key="your_preference_key"
    		android:defaultValue="0xff6699cc" 
    		app:supportsAlpha="true"
    		android:title="Pick a color with alpha" />
    </PreferenceScreen>
