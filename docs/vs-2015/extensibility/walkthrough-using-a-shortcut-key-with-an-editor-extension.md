---
title: 'Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung | Microsoft-Dokumentation'
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
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201946"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können in der Editor-Erweiterung auf Tastenkombinationen reagieren. In der folgenden exemplarischen Vorgehensweise wird veranschaulicht, wie einer Textansicht mit einer Tastenkombination ein Ansichts Zusatzelement hinzugefügt wird. Diese exemplarische Vorgehensweise basiert auf der Ansichts-Editor-Vorlage Viewport und ermöglicht das Hinzufügen des Zusatz Elements mit dem Zeichen +.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `KeyBindingTest` .  
  
2. Fügen Sie dem Projekt eine Editor-Text Zusatzelement Vorlage hinzu, und benennen Sie Sie `KeyBindingTest` . Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Fügen Sie die folgenden Verweise hinzu, und legen Sie **CopyLocal** auf fest `false` :  
  
    Microsoft. VisualStudio. Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft. VisualStudio. Shell. 14,0  
  
    Microsoft. VisualStudio. Text Manager. Interop  
  
   Ändern Sie in der keybindingtest-Klassendatei den Klassennamen in purplecornerbox. Verwenden Sie die Glühbirne, die am linken Rand angezeigt wird, um die anderen entsprechenden Änderungen vorzunehmen. Ändern Sie im Konstruktor den Namen der Zusatzelement-Ebene von **keybindingtest** in **purplecornerbox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definieren des Befehls Filters  
 Der Befehls Filter ist eine Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , die den Befehl verarbeitet, indem das Zusatzelement instanziiert wird.  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandFilter`.  
  
2. Fügen Sie die folgenden using-Anweisungen hinzu.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. Die Klasse mit dem Namen keybindingcommandfilter sollte von Erben <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. Fügen Sie private Felder für die Textansicht, den nächsten Befehl in der Befehlskette und ein Flag hinzu, um darzustellen, ob der Befehls Filter bereits hinzugefügt wurde.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5. Fügen Sie einen Konstruktor hinzu, der die Textansicht festlegt.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6. Implementieren Sie die- `QueryStatus()` Methode wie folgt.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Implementieren Sie die- `Exec()` Methode, sodass der Ansicht ein Violettes Feld hinzugefügt wird, wenn ein +-Zeichen eingegeben wird.  
  
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
  
## <a name="adding-the-command-filter"></a>Hinzufügen des Befehls Filters  
 Der Zusatzelement-Anbieter muss der Textansicht einen Befehls Filter hinzufügen. In diesem Beispiel implementiert der Anbieter, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> um auf die Erstellung von Text Ansichts Ereignissen zu lauschen. Dieser Zusatz Erstellungs Anbieter exportiert außerdem die Zusatzelement-Ebene, die die Z-Reihenfolge des Zusatz Elements definiert.  
  
1. Fügen Sie in der Datei keybindingtesttextviewkreationlistener die folgenden using-Anweisungen hinzu:  
  
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
  
2. Ändern Sie in der Zusatzelement-Ebenendefinition den Namen von adornmentlayer von **keybindingtest** in **purplecornerbox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Um den Text Ansichts Adapter zu erhalten, müssen Sie den importieren <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Ändern Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode so, dass Sie hinzugefügt wird `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. Der `AddCommandFilter` Handler Ruft den Text Ansichts Adapter ab und fügt den Befehls Filter hinzu.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Anzeigen des Zusatz Elements in jeder Zeile  
 Das ursprüngliche Zusatzelement wurde für jedes Zeichen "a" in einer Textdatei angezeigt. Nachdem Sie den Code so geändert haben, dass er das Zusatzelement als Reaktion auf das Zeichen "+" hinzufügt, wird das Zusatzelement nur für die Zeile hinzugefügt, in der das Zeichen "+" eingegeben wurde. Wir können den Zusatzelement Code so ändern, dass das Zusatzelement auf allen "a"-Werten wieder angezeigt wird.  
  
 Ändern Sie in der Datei KeyBindingTest.cs die Methode "foratevisuals ()", um alle Zeilen in der Ansicht zu durchlaufen, um das Zeichen "a" zu ergänzen.  
  
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
  
1. Erstellen Sie die Projekt Mappe "keybindingtest", und führen Sie Sie in der experimentellen Instanz aus.  
  
2. Erstellen oder öffnen Sie eine Textdatei. Geben Sie einige Wörter ein, die das Zeichen "a" enthalten, und geben Sie dann in der Textansicht den Text + irgendwo ein.  
  
     Ein Violettes Quadrat sollte auf jedem "a"-Zeichen in der Datei angezeigt werden.
