---
title: "Exemplarische Vorgehensweise: Verwenden einer Tastenkombination, mit der Erweiterung-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] link Tastatureingaben neu - Befehlen"
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Exemplarische Vorgehensweise: Verwenden einer Tastenkombination, mit der Erweiterung-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Tastenkombinationen in der Editor\-Erweiterung reagieren. Die folgende exemplarische Vorgehensweise veranschaulicht das Hinzufügen einer Ansicht Adornment auf eine Textansicht mithilfe einer Tastenkombination. Diese exemplarische Vorgehensweise basiert auf der Viewport Randsteuerelement\-Editor\-Vorlage, und es Ihnen das Zusatzelement mit hinzufügen das Zeichen \+.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts \(Managed Extensibility Framework\)  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `KeyBindingTest`.  
  
2.  Das Projekt eine Elementvorlage Editor Text Adornment hinzu, und nennen Sie es `KeyBindingTest`. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Fügen Sie die folgenden Verweise hinzu, und legen Sie **CopyLocal** auf `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 Ändern Sie den Klassennamen in der Klassendatei KeyBindingTest zu PurpleCornerBox. Verwenden Sie die Glühbirne, die angezeigt wird am linken Rand, um die entsprechenden Änderungen vornehmen. Innerhalb des Konstruktors ändern Sie den Namen der Ebene aus Randsteuerelement **KeyBindingTest** auf **PurpleCornerBox**:  
  
```c#  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## Der Befehlsfilter definieren  
 Der Befehlsfilter ist eine Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, mit dem Befehl durch Instanziieren das Zusatzelement behandelt.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `KeyBindingCommandFilter`.  
  
2.  Fügen Sie die folgenden using\-Anweisungen hinzu.  
  
    ```c#  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Die KeyBindingCommandFilter\-Klasse erbt, von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```c#  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Fügen Sie private Felder für die Textansicht, den nächsten Befehl in der Befehlskette und ein Flag, das darstellt, ob der Befehlsfilter bereits hinzugefügt wurde.  
  
    ```c#  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der die Textansicht festlegt.  
  
    ```c#  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementieren der `QueryStatus()` \-Methode wie folgt.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementieren der `Exec()` Methode, sodass die It ein Lila zur Ansicht Wenn Fügt eine \+ Zeichen eingegeben wird.  
  
    ```c#  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## Der Befehlsfilter hinzufügen  
 Zusatzelement Anbieter muss die Ansicht für den Befehlsfilter hinzufügen. In diesem Beispiel wird der Anbieter implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Ansicht Erstellungsereignisse überwacht. Dieser Anbieter Adornment exportiert Randsteuerelement der Ebene der Z\-Reihenfolge von den Adornment definiert.  
  
1.  Fügen Sie in der Datei KeyBindingTestTextViewCreationListener die folgende using\-Anweisungen:  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  In der Definition des Adornment Ebene, ändern Sie den Namen von der AdornmentLayer aus **KeyBindingTest** auf **PurpleCornerBox**.  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Um den Text\-Ansicht\-Adapter zu erhalten, müssen Sie importieren die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```c#  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Ändern der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass die It fügt die `KeyBindingCommandFilter`.  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  Die `AddCommandFilter` Handler Ruft den Text\-Ansicht\-Adapter ab und fügt der Befehlsfilter hinzu.  
  
    ```c#  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## Machen das Zusatzelement in jeder Zeile angezeigt werden  
 Das ursprüngliche Zusatzelement wurden für jedes Zeichen "a" in eine Textdatei. Nun, dass wir den Code zum Hinzufügen der Adornment als Antwort auf das Zeichen "\+" geändert haben, fügt es das Zusatzelement nur in der Zeile, in denen das "\+" typisiert ist. Wir können den Code Adornment ändern, sodass das Zusatzelement einmal angezeigt wird jede 'a'.  
  
 Ändern Sie in der Datei KeyBindingTest.cs die CreateVisuals\(\)\-Methode, um alle Zeilen in der Ansicht ergänzt das Zeichen "a" durchlaufen.  
  
```c#  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Erstellen und Testen des Codes  
  
1.  Erstellen Sie die Projektmappe KeyBindingTest, und führen Sie es in der experimentellen Instanz.  
  
2.  Erstellen Sie oder öffnen Sie eine Textdatei. Geben Sie einige Wörter, die mit dem Zeichen "a", und geben Sie an einer beliebigen Stelle in der Textansicht \+.  
  
     Ein lila Quadrat sollte jedes Zeichen "a" in der Datei angezeigt werden.