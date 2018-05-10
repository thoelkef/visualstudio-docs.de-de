---
title: 'Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit der Erweiterung-Editor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8f8a310832f0691b4bc4056baddeb1fbbad78f8
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit der Erweiterung-Editor
Sie können in der Editor-Erweiterung auf Tastenkombinationen reagieren. Die folgende exemplarische Vorgehensweise veranschaulicht das Hinzufügen einer Ansicht Randsteuerelement einer Text-Ansicht mit einer Tastenkombination. Diese exemplarische Vorgehensweise basiert auf der Viewport Randsteuerelement-Editor-Vorlage, und können Sie mithilfe der Randsteuerelement hinzufügen das Zeichen + enthält.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `KeyBindingTest`.  
  
2.  Das Projekt eine Elementvorlage Editor Text Zusatzelement (adornment) hinzu, und nennen Sie sie `KeyBindingTest`. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Fügen Sie die folgenden Verweise hinzu, und legen Sie **CopyLocal** auf `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 Ändern Sie den Klassennamen in PurpleCornerBox, in der Klassendatei KeyBindingTest. Verwenden Sie die Glühbirne, die angezeigt wird am linken Rand, um die entsprechenden andere Änderungen vornehmen. Innerhalb des Konstruktors, ändern Sie den Namen der Ebene Randsteuerelement aus **KeyBindingTest** auf **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

In der Klassendatei KeyBindingTestTextViewCreationListener.cs ändern Sie den Namen des der AdornmentLayer aus **KeyBindingTest** auf **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handling-typechar-command"></a>Behandlung von TYPECHAR-Befehl
Vor Visual Studio 2017 Version 15,6 war die einzige Möglichkeit zum Behandeln von Befehlen in eine Editor-Erweiterung implementiert ein <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> basierten Befehlsfilter. Visual Studio 2017 Version 15,6, einen modernen vereinfachten Ansatz ein basierend auf den Editor Befehlshandler eingeführt. In den nächsten beiden Abschnitten veranschaulichen, wie mithilfe von sowohl die ältere und moderne Ansatz einen Befehl zu behandeln.

## <a name="defining-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definieren den Befehlsfilter (vor Installation von Visual Studio-2017 Version 15,6)

 Der Befehlsfilter ist eine Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, den Befehl durch Instanziierung der Zusatzelement (adornment) behandelt.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandFilter`.  
  
2.  Fügen Sie die folgenden using-Anweisungen hinzu.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Die Klasse mit dem Namen KeyBindingCommandFilter Vererben sollte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Fügen Sie private Felder für die Text an, den nächsten Befehl in der Befehlskette und ein Flag, um darzustellen, ob der Befehlsfilter bereits hinzugefügt wurden.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der Textansicht festlegt.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementieren der `QueryStatus()` Methode wie folgt.  
  
    ```csharp  
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
  
## <a name="adding-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Hinzufügen des Filters Befehl (vor Installation von Visual Studio-2017 Version 15,6)
 Zusatzelement (adornment)-Anbieter muss einen Befehlsfilter Textansicht hinzufügen. In diesem Beispiel wird vom Anbieter implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , Text-Erstellung sichtereignisse zu überwachen. Dieser Anbieter Randsteuerelement exportiert Zusatzelement (adornment) der Ebene der Z-Reihenfolge von der Zusatzelement (adornment) definiert.  
  
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
  
2.  Um den Text-Ansicht-Adapter zu erhalten, müssen Sie importieren die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Ändern der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass die It fügt die `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  Die `AddCommandFilter` Handler Ruft den Text anzeigen Adapter ab, und der Befehlsfilter hinzugefügt.  
  
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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementieren der Befehlshandler (in Visual Studio 2017 Version 15,6 ab)

Aktualisieren Sie zuerst den Verweisen des Projekts Nuget um den neuesten-Editor-API zu verweisen:

1. Mit der rechten Maustaste auf das Projekt, und wählen **NuGet-Pakete verwalten**.

2. In **Nuget Package Manager**, wählen die **Updates** Registerkarte die **wählen Sie alle Pakete** Kontrollkästchen, und wählen Sie dann **Update**.

Der Befehlshandler ist eine Implementierung von <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, den Befehl durch Instanziierung der Zusatzelement (adornment) behandelt.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandHandler`.  
  
2.  Fügen Sie die folgenden using-Anweisungen hinzu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Commanding;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;   
    ```  
  
3.  Die Klasse mit dem Namen KeyBindingCommandHandler Vererben sollte `ICommandHandler<TypeCharCommandArgs>`, und exportieren Sie es als <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
    ```csharp  
    [Export(typeof(ICommandHandler))]
    [ContentType("text")]
    [Name("KeyBindingTest")]
    internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
    ```  
  
4.  Fügen Sie einen Anzeigenamen der Befehlshandler hinzu:  
  
    ```csharp  
    public string DisplayName => "KeyBindingTest";
    ```  
    
5.  Implementieren der `GetCommandState()` Methode wie folgt. Da diese Befehlshandler Core Editor TYPECHAR-Befehl verarbeitet, können sie delegieren, aktivieren den Befehl aus, um die Core-Editor.
  
    ```csharp  
    public CommandState GetCommandState(TypeCharCommandArgs args)
    {
        return CommandState.Unspecified;
    } 
    ```  
  
6.  Implementieren der `ExecuteCommand()` Methode, sodass die It eine violette Box auf die Ansicht Wenn Fügt eine + Zeichen eingegeben wird. 
  
    ```csharp  
    public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
    {
        if (args.TypedChar == '+')
        {
            bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
                "KeyBindingTextAdorned", out bool adorned) && adorned;
            if (!alreadyAdorned)
            {
                new PurpleCornerBox((IWpfTextView)args.TextView);
                args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
            }
        }

        return false;
    }
    ```  
 7. Kopieren Sie Zusatzelement (adornment) Ebene Definition aus KeyBindingTestTextViewCreationListener.cs-Datei in die KeyBindingCommandHandler.cs zu und löschen Sie KeyBindingTestTextViewCreationListener.cs-Datei:
 
    ```csharp  
    /// <summary>
    /// Defines the adornment layer for the adornment. This layer is ordered
    /// after the selection layer in the Z-order.
    /// </summary>
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("PurpleCornerBox")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    private AdornmentLayerDefinition editorAdornmentLayer;    
    ```  

## <a name="making-the-adornment-appear-on-every-line"></a>Machen die Zusatzelement (adornment) in jeder Zeile angezeigt werden  

Die ursprüngliche Randsteuerelement schien für jedes Zeichen "a" in eine Textdatei. Nun, dass wir den Code zum Hinzufügen der Randsteuerelement als Antwort auf das Zeichen "+" geändert haben, fügt Sie der Zusatzelement (adornment) nur in der Zeile, in dem die "+" typisiert ist. Wir können den Randsteuerelement-Code ändern, sodass die Randsteuerelement einmal auf angezeigt wird jede "a".  
  
Ändern Sie in der Datei KeyBindingTest.cs die CreateVisuals()-Methode, um alle Zeilen in der Sicht ergänzt das Zeichen "a" durchlaufen.  
  
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
  
2.  Erstellen Sie oder öffnen Sie eine Textdatei. Geben Sie einige Wörter, die das Zeichen "a", und geben Sie dann + an einer beliebigen Stelle in der Textansicht.  
  
     Eine violette Quadrat sollte auf jedem Zeichen "a" in der Datei angezeigt werden.
