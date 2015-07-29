---
title: Design Time
page_title: Design Time | UI for WinForms Documentation
description: Design Time
slug: winforms/telerik-presentation-framework/printing-support/radprintdocument/design-time
tags: design,time
published: True
position: 0
---

# Design Time



## 

To start using RadPrintDocument at design time, drag it from the toolbox and drop it on the form.
        	It will appear as a component, so you can select it and edit its properties either through the
        	property window of Visual Studio, or by using its smart tag menu.
        

![tpf-printing-support-radprintdocument-design-time](images/tpf-printing-support-radprintdocument-design-time.png)

In the smart tag menu, you can associate the RadPrintDocument with an object that supports
  			printing (i.e. which implements the __IPrintable__ interface) by choosing
  			it from the __Printed Object__ drop-down. You can also setup the header 
  			and the footer of each page by setting a height value and a text for each part of the header/footer.
  			If the__Reverse on Even Pages__ option is enabled, then the places of the 
  			__Left Text__and the __Right Text__will be swapped on pages with an even number.
  		

To edit settings, specific for the selected printable object, click on the __Settings__
  			button in the smart tag menu. This will open the RadPrintSettingsDialog corresponding to the selected
  			printable object. You can use its full functionality to setup printing
  			settings at design time. More information about RadPrintSettingsDialog in 
  			 [this article]({%slug winforms/telerik-presentation-framework/printing-support/end-user-functionality/print-settings-dialog%}).        	 
  		