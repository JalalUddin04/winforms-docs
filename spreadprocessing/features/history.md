---
title: History
page_title: History | UI for WinForms Documentation
description: History
slug: winforms/spreadprocessing/features/history
tags: history
published: True
position: 7
previous_url: spreadprocessing-features-history
---

# History

The document model maintains a history stack that tracks all changes to the content of the workbook. The history is implemented via the __WorkbookHistory__ class and the __Workbook__ exposes a property of this type. All changes introduced to the workbook are automatically recorded, however, the model also allows manual control over the history.

* [Undo / Redo Actions](#undo-/-redo-actions)

* [Smart Undo](#smart-undo)

* [Enable / Disable History](#enable-/-disable-history)

* [Clear History](#clear-history)

## Enable / Disable History

By default the __WorkbookHistory__ class does not record all changes introduced to the workbook, but there are scenarios that need the history feature. For example, if you construct an entire document from code behind, you do not need to record each action you perform. In such cases you do not need to enable the history for the workbook via the __IsEnabled__ property of the __WorkbookHistory__ class. However, if you want to be able to undo one or several of the recent changes, you would need to enable the history.

__Example 1__ enables the history of a workbook.

#### Example 1: Enable history

{{source=..\SamplesCS\RadSpreadProcessing\Features\RadSpreadProcessingHistory.cs region=radspreadprocessing-features-history_2}} 
{{source=..\SamplesVB\RadSpreadProcessing\Features\RadSpreadProcessingHistory.vb region=radspreadprocessing-features-history_2}} 

````C#
Workbook workbook = new Workbook();
workbook.History.IsEnabled = false;

````
````VB.NET
Dim workbook As New Workbook()
workbook.History.IsEnabled = False

````

{{endregion}} 

>warning The default value of the IsEnabled property was changed in R3 2014. In versions prior that one, the history is enabled by default.
>

## Undo / Redo Actions

Once the hisory is enabled you can invoke its __Undo()__ and __Redo()__ methods to perform undo and redo actions respectively. Both methods return a __Boolean__ value that indicates whether the operations were successful. The __Workbook__ class exposes the *Boolean* properties __CanUndo__ and __CanRedo__ that indicate whether the respective action is applicable.
        

__Example 2__ creates a new workbook with a single worksheet and sets the value of cell *A1* twice. Further, the snippet performs the undo and redo actions.

#### Example 2: Perform undo and redo

{{source=..\SamplesCS\RadSpreadProcessing\Features\RadSpreadProcessingHistory.cs region=radspreadprocessing-features-history_0}} 
{{source=..\SamplesVB\RadSpreadProcessing\Features\RadSpreadProcessingHistory.vb region=radspreadprocessing-features-history_0}} 

````C#
Workbook workbook = new Workbook();        
Worksheet worksheet = workbook.Worksheets.Add(); 
workbook.History.IsEnabled = true;
worksheet.Cells[0, 0].SetValue("First cell value");
worksheet.Cells[0, 0].SetValue("Second cell value");
workbook.History.Undo();
workbook.History.Redo();

````
````VB.NET
Dim workbook As New Workbook()
Dim worksheet As Worksheet = workbook.Worksheets.Add()
workbook.History.IsEnabled = True
worksheet.Cells(0, 0).SetValue("First cell value")
worksheet.Cells(0, 0).SetValue("Second cell value")
workbook.History.Undo()
workbook.History.Redo()

````

{{endregion}} 

## Smart Undo

The __Workbook__ history offers a friendly API that allows grouping multiple changes into one undo step. For example, you may want to set the value of a cell and apply formatting to the same cell, and treat these two actions as a single undo operation. This can be easily achieved through enclosing the assignments with __BeginUndoGroup()__ and __EndUndoGroup()__ methods.

__Example 3__ demonstrates how to create an undo group:
        
#### Example 3: Create undo group

{{source=..\SamplesCS\RadSpreadProcessing\Features\RadSpreadProcessingHistory.cs region=radspreadprocessing-features-history_1}} 
{{source=..\SamplesVB\RadSpreadProcessing\Features\RadSpreadProcessingHistory.vb region=radspreadprocessing-features-history_1}} 

````C#
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets.Add();
workbook.History.IsEnabled = true;
workbook.History.BeginUndoGroup();
worksheet.Cells[0, 0].SetValue(15);
worksheet.Cells[0, 0].SetFormat(new CellValueFormat("0.00"));
workbook.History.EndUndoGroup();
workbook.History.Undo();
workbook.History.Redo();

````
````VB.NET
Dim workbook As New Workbook()
Dim worksheet As Worksheet = workbook.Worksheets.Add()
workbook.History.IsEnabled = True
workbook.History.BeginUndoGroup()
worksheet.Cells(0, 0).SetValue(15)
worksheet.Cells(0, 0).SetFormat(New CellValueFormat("0.00"))
workbook.History.EndUndoGroup()
workbook.History.Undo()
workbook.History.Redo()

````

{{endregion}} 

## Clear History

To clear the history you just have to call the __Clear()__ method of the __WorkbookHistory__ class. Note that you cannot clear the history if you are recording an undo group. If you attempt to call the method after invoking __BeginUndoGroup()__ an exception is be thrown. The following snippet illustrates how to clear workbook's history.

__Example 4__ clears the history of a workbook.

#### Example 4: Clear history.

{{source=..\SamplesCS\RadSpreadProcessing\Features\RadSpreadProcessingHistory.cs region=radspreadprocessing-features-history_3}} 
{{source=..\SamplesVB\RadSpreadProcessing\Features\RadSpreadProcessingHistory.vb region=radspreadprocessing-features-history_3}} 

````C#
Workbook workbook = new Workbook();
workbook.History.Clear();

````
````VB.NET
Dim workbook As New Workbook()
workbook.History.Clear()

````

{{endregion}}
