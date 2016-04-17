+++
date = "2015-04-02T14:48:15-04:00"
title = "Creating accessible controls with Xamarin.Forms"
description = "Custom renderers aren't that difficult"
+++

Xamarin Forms is [marketed](https://developer.xamarin.com/guides/xamarin-forms/#Is_Xamarin.Forms_right_for_your_project) as a tool for simple data entry apps and prototyping, but wtih a little bit of knowledge, Forms can work for a cross platform app.

One thing that Forms lacks on its controls is access to the accessibility features that are necessary for your app to be usable by screen reader users. However, adding that capability is very easy.

I'm going to walk through adding accessible labels to buttons. The first thing we need is a new control, since [Button](https://developer.xamarin.com/api/type/Xamarin.Forms.Button/) doesn't allow us to show text to a screen reader on an image button. This is a Forms control, so put it into the cross-platform project of your Forms solution

{{< gist c6b6c7cc215ced10d3f22d34ed721356 >}} 


We just extend the Forms button with a bindable property, and we're done with the control.

We need to do a similar thing with the Xamarin renderer. Here's an implementation of a renderer that uses the bindable property from our AccessibleButton and sets the value eo the Android control's ContentDescription proprety, which is visible to screen reader users on Android. This renderer is an Android renderer, so it goes into the Android project of your Forms solution.

One other detail we need to set on the renderer, we need to export our renderer so that it actually gets used to render our Forms controls. we need this line outside the namespace declaration in our Renderer's file. 

{{< gist 2fef6f53522161be761dfbc22c33264e >}} 

Then, you can use this within a Forms page just like any other Forms control

<code class='xml'>
	  &lt;btn:AccessibleButton Text=&quot;This shows on the screen&quot; AccessibleText=&quot;This is read by talkback&quot; ....
</code>