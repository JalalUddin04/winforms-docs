---
title: Using RtfFormatProvider
page_title: Using RtfFormatProvider | UI for WinForms Documentation
description: Using RtfFormatProvider
slug: winforms/wordsprocessing/formats-and-conversion/rtf/using-rtfformatprovider
tags: using,rtfformatprovider
published: True
position: 1
previous_url: wordsprocessing-formats-and-conversion-rtf-using-rtfformatprovider
---

# Using RtfFormatProvider

__RtfFormatProvider__ makes it easy to import and export __RadFlowDocument__ to/from RTF format, preserving the entire document structure and formatting.

All you have to do in order to use __RtfFormatProvider__ is add references to the assemblies listed below:
      

* Telerik.Windows.Documents.Core.dll
          

* Telerik.Windows.Documents.Flow.dll
          

## Import

In order to import an RTF document you need to use the __Import()__ method of __RtfFormatProvider__.

The following code snippet shows how to use __RtfFormatProvider__ to import an RTF document from a file:

{{source=..\SamplesCS\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.cs region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_0}} 
{{source=..\SamplesVB\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.vb region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_0}} 

````C#
RtfFormatProvider provider = new RtfFormatProvider();
using (Stream input = File.OpenRead("Sample.rtf"))
{
    RadFlowDocument document = provider.Import(input);
}

````
````VB.NET
Dim provider As New RtfFormatProvider()
Using input As Stream = File.OpenRead("Sample.rtf")
    Dim document As RadFlowDocument = provider.Import(input)
End Using

````

{{endregion}} 

And here is how you can import a document from string containing the RTF document:

{{source=..\SamplesCS\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.cs region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_1}} 
{{source=..\SamplesVB\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.vb region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_1}} 

````C#
RtfFormatProvider provider = new RtfFormatProvider();
RadFlowDocument document = provider.Import(input);

````
````VB.NET
Dim provider As New RtfFormatProvider()
Dim document As RadFlowDocument = provider.Import(input)

````

{{endregion}} 

The resulting __RadFlowDocument__ can be used like any code-generated document.

## Export

In order to export a document to RTF you need to use the __Export()__ method of __RtfFormatProvider__.

The following snippet shows how to use __RtfFormatProvider__ to export __RadFlowDocument__ to a file.

{{source=..\SamplesCS\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.cs region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_2}} 
{{source=..\SamplesVB\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.vb region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_2}} 

````C#
RtfFormatProvider provider = new RtfFormatProvider();
using (Stream output = File.Create("sample.rtf"))
{
    RadFlowDocument document = CreateRadFlowDocument();
    provider.Export(document, output);
}

````
````VB.NET
Dim provider As New RtfFormatProvider()
Using output As Stream = File.Create("sample.rtf")
    Dim document As RadFlowDocument = CreateRadFlowDocument()
    provider.Export(document, output)
End Using

````

{{endregion}} 

You can also export the document to a string and preserve it in a database.

{{source=..\SamplesCS\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.cs region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_3}} 
{{source=..\SamplesVB\WordsProcessing\FormatsAndConversion\Rtf\WordsProcessingUsingrtfFormatProvider.vb region=radwordsprocessing-formats-and-conversion-rtf-rtfformatprovider_3}} 

````C#
RtfFormatProvider provider = new RtfFormatProvider();
RadFlowDocument document = CreateRadFlowDocument();
string output = provider.Export(document);

````
````VB.NET
Dim provider As New RtfFormatProvider()
Dim document As RadFlowDocument = CreateRadFlowDocument()
Dim output As String = provider.Export(document)

````

{{endregion}} 

The resulting documents can be opened in any application that supports RTF documents.
        
