---
title: 'Exemplarische Vorgehensweise: Verwenden eine Tastenkombination mit einer Editor-Erweiterung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b40c0590b19b555f757af1e0a38481b0b245c07d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956061"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können in die editorerweiterung auf Tastenkombinationen reagieren. Die folgende exemplarische Vorgehensweise veranschaulicht das Hinzufügen einer Ansicht Zusatzelement auf eine Textansicht mit einer Tastenkombination. Diese exemplarische Vorgehensweise basiert auf der Viewport Zusatzelement-Editor-Vorlage, und es Ihnen, fügen das Zusatzelement mit den Zeichen +.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
1. Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `KeyBindingTest`.  
  
2. Das Projekt eine Elementvorlage Editor Text Zusatzelement hinzu, und nennen Sie sie `KeyBindingTest`. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Fügen Sie die folgenden Verweise hinzu, und legen Sie **CopyLocal** zu `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   Ändern Sie den Namen der Klasse in PurpleCornerBox, in der Datei KeyBindingTest-Klasse. Verwenden Sie die Glühbirne verlagert, die angezeigt wird am linken Rand, um die andere entsprechende Änderungen vornehmen. Ändern Sie innerhalb des Konstruktors den Namen der die Zusatzelementebene aus **KeyBindingTest** zu **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Den Befehlsfilter definieren  
 Der Befehlsfilter ist eine Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, behandelt den Befehl durch Instanziieren des Zusatzelements ab.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandFilter`.  
  
2.  Fügen Sie die folgenden using-Anweisungen hinzu.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Die Klasse, die mit dem Namen KeyBindingCommandFilter erben soll <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Fügen Sie private Felder für die Textansicht, in den nächsten Befehl in der Befehlskette, und ein Flag zum angeben, ob der Befehlsfilter wurde bereits hinzugefügt.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der die Textansicht festlegt.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementieren der `QueryStatus()` -Methode wie folgt.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementieren der `Exec()` Methode, sodass die It eine violette Box auf die Ansicht Wenn Fügt eine + Zeichen eingegeben wird.  
  
    ```csharp  
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
  
## <a name="adding-the-command-filter"></a>Den Befehlsfilter hinzufügen  
 Der zusatzelementanbieter muss einen Befehlsfilter der Textansicht hinzufügen. In diesem Beispiel ist der Anbieter implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> zum Lauschen auf Ereignisse beim Erstellen von Text anzeigen. Dieser zusatzelementanbieter exportiert auch die Zusatzelementebene, die die Z-Reihenfolge des Zusatzelements definiert.  
  
1.  Fügen Sie in der Datei KeyBindingTestTextViewCreationListener die folgenden using-Anweisungen:  
  
    ```csharp  
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
  
2.  In der Definition des Zusatzelements Ebene ändern Sie den Namen der der AdornmentLayer aus **KeyBindingTest** zu **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Um der Textansichtsadapter zu erhalten, müssen Sie importieren die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Ändern der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass die It fügt die `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  Die `AddCommandFilter` Handler ruft der Textansichtsadapter, und der Befehlsfilter hinzugefügt.  
  
    ```csharp  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Das Zusatzelement vornehmen in jeder Zeile angezeigt werden  
 Das ursprüngliche Zusatzelement angezeigt wird, für jedes enthaltene Zeichen "a" in eine Textdatei. Nun, dass wir den Code zum Hinzufügen des Zusatzelements in Reaktion auf das Zeichen "+" geändert haben, fügt er das Zusatzelement nur in der Zeile, in dem die "+" typisiert ist. Ändern wir den Code des Zusatzelements, damit das Zusatzelement noch einmal auf angezeigt wird jedes "a".  
  
 Ändern Sie in der Datei KeyBindingTest.cs die CreateVisuals()-Methode, die alle Zeilen in der Ansicht, um das Zeichen "a" ergänzen durchlaufen.  
  
```csharp  
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
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
  
1.  Erstellen Sie die KeyBindingTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
2.  Erstellen Sie oder öffnen Sie eine Textdatei. Geben Sie einige Wörter, die mit dem Zeichen "a", und geben Sie dann + an einer beliebigen Stelle in der Textansicht.  
  
     Eine violette Quadrat sollte auf jedem Zeichen "a" in der Datei angezeigt werden.
