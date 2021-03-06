---
title: RadFlowDocument
page_title: RadFlowDocument | UI for WinForms Documentation
description: RadFlowDocument
slug: winforms/wordsprocessing/model/radflowdocument
tags: radflowdocument
published: True
position: 0
previous_url: wordsprocessing-model-radflowdocument
---

# RadFlowDocument

__RadFlowDocument__ hosts flow document content and is the root elements in the document elements tree. It holds a collection of [Section](ca452231-3afc-45d0-b0f8-91404d6c52a2) elements.
      

* [Inserting and Modifying a RadFlowDocument](#inserting-and--modifying-a-radflowdocument)

* [Operating with a RadFlowDocument](#operating-with-a-radflowdocument)

## Inserting and  Modifying a RadFlowDocument

The following code snippet shows how you can create a new __RadFlowDocument__:

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRadFlowDocument.cs region=radwordsprocessing-model-radflowdocument_0}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRadFlowDocument.vb region=radwordsprocessing-model-radflowdocument_0}} 

````C#
RadFlowDocument document = new RadFlowDocument();

````
````VB.NET
Dim document As New RadFlowDocument()

````

{{endregion}} 

__RadFlowDocument__ exposes properties which allow you to customize the way content is presented. The following properties are available for change:

* __ViewType__: An enumeration which specifies how the document should be laid out when displayed. It depends on the application with which the document is opened after it has been created whether this property is respected.

* __Theme__: Specifies the theme which is applied on the document. The document theme enables you to specify colors, fonts and a variety of graphic effects which affect the look of the whole document. More information is available [here]({%slug winforms/wordsprocessing/concepts/document-themes%}).

* __StyleRepository__: Represents the document' StyleRepository. The repository allows to add, remove or enumerate the styles of the document.

* __DefaultStyle__: The default styles that are used for __Paragraph__ and __Run__ elements. More information on default styles is available [here]({%slug winforms/wordsprocessing/concepts/styles%}).

* __HasDifferentEvenOddPageHeadersFooters__: Gets or sets whether pages in this document should have different headers and footers for even and odd pages.

* __ListCollection__: Represents the collection of [Lists]({%slug winforms/wordsprocessing/concepts/lists%}) in the document.

* __CommentCollection__: Represents the collection of [Comments]({%slug winforms/wordsprocessing/model/comment%}) in the document.

## Operating with a RadFlowDocument

There are different actions which you can execute with the help of the __RadFlowDocument__ element.

### Adding Sections

You can create a __RadFlowDocument__ from scratch and add Sections to it as follows:

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRadFlowDocument.cs region=radwordsprocessing-model-radflowdocument_1}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRadFlowDocument.vb region=radwordsprocessing-model-radflowdocument_1}} 

````C#
RadFlowDocument document = new RadFlowDocument();
document.Sections.AddSection();

````
````VB.NET
Dim document As New RadFlowDocument()
document.Sections.AddSection()

````

{{endregion}} 

The Sections property of the document is of type __SectionCollection__ and allows you to add sections to the document.

Alternatively, you could create a section by passing to its constructor the document it should be associated with.

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRadFlowDocument.cs region=radwordsprocessing-model-radflowdocument_2}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRadFlowDocument.vb region=radwordsprocessing-model-radflowdocument_2}} 

````C#
Section section = new Section(document);

````
````VB.NET
Dim section As New Section(document)

````

{{endregion}} 

### Merge with Another Document

You can merge a __RadFlowDocument__ within another document by using the __Merge()__ method and pass the source document as a parameter to it:

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRadFlowDocument.cs region=radwordsprocessing-model-radflowdocument_3}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRadFlowDocument.vb region=radwordsprocessing-model-radflowdocument_3}} 

````C#
document.Merge(sourceDocument);

````
````VB.NET
document.Merge(sourceDocument)

````

{{endregion}}

Additionally, you have the opportunity to specify the __MergeOptions__ which control the merge operation:

* __ConflictingStylesResolutionMode__: An enumeration specifying the mode used for resolving conflicts between styles with same IDs. The possible values for ConflictingStylesResolutionMode are:
                

* __UseTargetStyle__: If a conflict between styles with the same IDs appears, the style of the __target__ document is used.
                    

* __RenameSourceStyle__: If a conflict between styles with the same IDs appears, the style of the  __source__ document is renamed and used.

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRadFlowDocument.cs region=radwordsprocessing-model-radflowdocument_4}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRadFlowDocument.vb region=radwordsprocessing-model-radflowdocument_4}} 

````C#
MergeOptions mergeOptions = new MergeOptions();
mergeOptions.ConflictingStylesResolutionMode = ConflictingStylesResolutionMode.RenameSourceStyle;
document.Merge(sourceDocument, mergeOptions);

````
````VB.NET
Dim mergeOptions As New MergeOptions()
mergeOptions.ConflictingStylesResolutionMode = ConflictingStylesResolutionMode.RenameSourceStyle
document.Merge(sourceDocument, mergeOptions)

````

{{endregion}} 

### Update Fields

__RadFlowDocument__ exposes a __UpdateFields()__ method which allows you to update all fields in the document. More information about fields is available [here](6421f63c-7a33-4fdd-96bb-eda83bc198bf).

The next snippet shows how all fields in a document can be updated simultaneously.

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRadFlowDocument.cs region=radwordsprocessing-model-radflowdocument_5}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRadFlowDocument.vb region=radwordsprocessing-model-radflowdocument_5}} 

````C#
document.UpdateFields();

````
````VB.NET
document.UpdateFields()

````

{{endregion}} 

# See Also

 * [RadFlowDocument API Reference](http://www.telerik.com/help/winforms/allmembers_t_telerik_windows_documents_flow_model_radflowdocument.html)

 * [Document model]({%slug winforms/wordsprocessing/model%})
