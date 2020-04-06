---
title: 'Exemplarische Vorgehensweise: Verwenden eines Shortcut-Schlüssels mit einer Editorerweiterung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697149"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editorerweiterung
Sie können auf Tastenkombinationen in der Editor-Erweiterung antworten. In der folgenden exemplarischen Vorgehensweise wird gezeigt, wie Sie einer Textansicht mithilfe einer Tastenkombination eine Ansichtsverzierung hinzufügen. Diese exemplarische Vorgehensweise basiert auf der Vorlage für den Ansichtsfenster-Verzierungs-Editor und ermöglicht es Ihnen, die Verzierung mithilfe des Zeichens + hinzuzufügen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `KeyBindingTest`die Lösung .

2. Fügen Sie dem Projekt eine Editor Text `KeyBindingTest`Adornment-Elementvorlage hinzu, und benennen Sie sie . Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Fügen Sie die folgenden Verweise `false`hinzu, und legen Sie **CopyLocal** auf:

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   Ändern Sie in der KeyBindingTest-Klassendatei den Klassennamen in PurpleCornerBox. Verwenden Sie die Glühbirne, die am linken Rand angezeigt wird, um die anderen entsprechenden Änderungen vorzunehmen. Ändern Sie im Konstruktor den Namen des Verzierungs-Layers von **KeyBindingTest** in **PurpleCornerBox:**

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Ändern Sie in der KeyBindingTestTextViewCreationListener.cs Klassendatei den Namen des AdornmentLayer von **KeyBindingTest** in **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Handle TYPECHAR-Befehl
Vor Visual Studio 2017 Version 15.6 war die einzige Möglichkeit, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehle in einer Editorerweiterung zu behandeln, die Implementierung eines basierten Befehlsfilters. Visual Studio 2017 Version 15.6 führte einen modernen vereinfachten Ansatz ein, der auf Editorbefehlshandlern basiert. In den nächsten beiden Abschnitten wird veranschaulicht, wie ein Befehl sowohl mit dem legacy als auch mit dem modernen Ansatz behandelt wird.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definieren des Befehlsfilters (vor Visual Studio 2017 Version 15.6)

 Der Befehlsfilter ist <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>eine Implementierung von , die den Befehl verarbeitet, indem die Verzierung instanziiert wird.

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandFilter`.

2. Fügen Sie die folgenden Anweisungen mithilfe von Direktiven hinzu.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. Die Klasse mit dem Namen KeyBindingCommandFilter sollte von <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>erben.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Fügen Sie private Felder für die Textansicht, den nächsten Befehl in der Befehlskette und ein Flag hinzu, um darzustellen, ob der Befehlsfilter bereits hinzugefügt wurde.

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

6. Implementieren `QueryStatus()` Sie die Methode wie folgt.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implementieren `Exec()` Sie die Methode so, dass sie der Ansicht**+** ein violettes Feld hinzufügt, wenn ein Pluszeichen ( ) eingegeben wird.

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Hinzufügen des Befehlsfilters (vor Visual Studio 2017 Version 15.6)
 Der Verzierungsanbieter muss der Textansicht einen Befehlsfilter hinzufügen. In diesem Beispiel implementiert <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> der Anbieter, um Textansichterstellungsereignisse zu hören. Dieser Verzierungsanbieter exportiert auch den Verzierungs-Layer, der die Z-Reihenfolge der Verzierung definiert.

1. Fügen Sie in der Datei KeyBindingTestTextViewCreationListener Folgendes mithilfe von Direktiven hinzu:

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

2. Um den Textansichtsadapter abzubekommen, müssen Sie die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>importieren.

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Ändern <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Sie die Methode `KeyBindingCommandFilter`so, dass sie die hinzufügt.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Der `AddCommandFilter` Handler ruft den Textansichtsadapter ab und fügt den Befehlsfilter hinzu.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementieren eines Befehlshandlers (ab Visual Studio 2017 Version 15.6)

Aktualisieren Sie zunächst die Nuget-Referenzen des Projekts, um auf die neueste Editor-API zu verweisen:

1. Klicken Sie mit der rechten Maustaste auf das Projekt und wählen **Nuget-Pakete verwalten**aus.

2. Wählen Sie im **Nuget Package Manager**die Registerkarte **Updates** aus, aktivieren Sie das Kontrollkästchen Alle **Pakete auswählen,** und wählen Sie dann **Aktualisieren**aus.

Der Befehlshandler ist <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>eine Implementierung von , die den Befehl verarbeitet, indem die Verzierung instanziiert wird.

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandHandler`.

2. Fügen Sie die folgenden Anweisungen mithilfe von Direktiven hinzu.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Die Klasse mit dem Namen KeyBindingCommandHandler sollte `ICommandHandler<TypeCharCommandArgs>` <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>von erben und sie als exportieren:

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Fügen Sie einen Anzeigenamen des Befehlshandlers hinzu:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implementieren `GetCommandState()` Sie die Methode wie folgt. Da dieser Befehlshandler den Core-Editor-TYPCHAR-Befehl verarbeitet, kann er die Aktivierung des Befehls an den Kerneditor delegieren.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementieren `ExecuteCommand()` Sie die Methode so, dass sie der Ansicht**+** ein violettes Feld hinzufügt, wenn ein Pluszeichen ( ) eingegeben wird.

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

   7. Kopieren Sie die Definition des Verzierungs-Layers aus *KeyBindingTestTextViewCreationListener.cs* Datei in die *KeyBindingCommandHandler.cs,* und löschen Sie dann *KeyBindingTestTextViewCreationListener.cs* Datei:

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

## <a name="make-the-adornment-appear-on-every-line"></a>Lassen Sie die Verzierung in jeder Zeile erscheinen

Die ursprüngliche Verzierung erschien auf jedem Zeichen "a" in einer Textdatei. Nachdem wir den Code geändert haben, um die **+** Verzierung als Antwort auf das **+** Zeichen hinzuzufügen, fügt er die Verzierung nur in der Zeile hinzu, in der das Zeichen eingegeben wird. Wir können den Verzierungscode so ändern, dass die Verzierung wieder auf jedem 'a' angezeigt wird.

Ändern *Sie* in der `CreateVisuals()` KeyBindingTest.cs Datei die Methode, um alle Zeilen in der Ansicht zu durchlaufen, um das Zeichen "a" zu dekorieren.

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

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes

1. Erstellen Sie die KeyBindingTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

2. Erstellen oder öffnen Sie eine Textdatei. Geben Sie einige Wörter ein, die **+** das Zeichen 'a' enthalten, und geben Sie dann eine beliebige Stelle in der Textansicht ein.

     Ein violettes Quadrat sollte auf jedem "a"-Zeichen in der Datei angezeigt werden.
