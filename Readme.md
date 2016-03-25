# RichTextBlock.Html2Xaml

## Introduction

This is a fork of MacawNL/WinRT-RichTextBlock.Html2Xaml. It has been changed to a Windows runtime Component, making it usable with all languages, including C++. In addition, I have assured it works with UWP. 

The UWP RichTextBlock control serves to display read-only rich formatted text.
However, it supports a limited subset of XAML, and no HTML.

In scenario's where you want to display a field that contains HTML rich 
formatted text (e.g. when you have clients on multiple platforms, such as 
web, WinRT, iOS and Android), this package offers an alternative to 
using an embedded browser control. Using a browser control impacts 
performance and limits the UI experience (e.g. the WebView 
control does not support transparency).

**RichTextBlock.Html2Xaml** adds an Html extension property to RichTextBlock 
controls, that you can set (or data bind) to a string containing an Html 
snippet.

## Functionality
The RichTextBlock control only supports a limited set of XAML; this package
supports translating an equivalent limited set of HTML markup via an XSLT. 
The XSLT allows for simple modification or extension of the XAML to HTML
conversion. Any unsupported HTML tags will be discarded, but their text content
will be displayed.

The extension property is implemented in two simple source files that can be 
modified easily: one C# and one XSLT source file, no binaries.

## Distribution: NuGet

The UWP fork does not have a NuGet package yet, partly because I don't really know how to work with NuGet yet. If anyone wants to contribute to update the NuGet related files to UWP, that would be great

## Usage
1) In a XAML file, declare the namespace of the Common folder in your project, e.g.:
   `xmlns:common="using:Html2Xaml"`
    
2) In RichTextBlock controls, set or databind the Html property, e.g.:
  > `<RichTextBlock common:Properties.Html="{Binding ...}"/>` or
`    <RichTextBlock>
 		<common:Properties.Html>
 			<![CDATA[
 				<p>This is a list:</p>
 				<ul>
 					<li>Item 1</li>
 					<li>Item 2</li>
 					<li>Item 3</li>
 				</ul>
 			]]>
 		</common:Properties.Html>
    </RichTextBlock>
`
