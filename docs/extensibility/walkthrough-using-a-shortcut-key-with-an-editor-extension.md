---
title: 'Exemplarische Vorgehensweise: Verwenden eine Tastenkombination mit einer Editor-Erweiterung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d2abc185d06aa74e47bb2a36bd17df12a9db5c8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710304"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Exemplarische Vorgehensweise: Verwenden Sie eine Tastenkombination mit einer Editor-Erweiterung
Sie können in die editorerweiterung auf Tastenkombinationen reagieren. Die folgende exemplarische Vorgehensweise veranschaulicht das Hinzufügen einer Ansicht Zusatzelement auf eine Textansicht mit einer Tastenkombination. Diese exemplarische Vorgehensweise basiert auf der Viewport Zusatzelement-Editor-Vorlage, und es Ihnen, fügen das Zusatzelement mit den Zeichen +.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen Sie ein Projekt mit Managed Extensibility Framework (MEF)

1. Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `KeyBindingTest`.

2. Das Projekt eine Elementvorlage Editor Text Zusatzelement hinzu, und nennen Sie sie `KeyBindingTest`. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Fügen Sie die folgenden Verweise hinzu, und legen Sie **CopyLocal** zu `false`:

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   Ändern Sie den Namen der Klasse in PurpleCornerBox, in der Datei KeyBindingTest-Klasse. Verwenden Sie die Glühbirne verlagert, die angezeigt wird am linken Rand, um die andere entsprechende Änderungen vornehmen. Ändern Sie innerhalb des Konstruktors den Namen der die Zusatzelementebene aus **KeyBindingTest** zu **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Ändern Sie in der Datei KeyBindingTestTextViewCreationListener.cs-Klasse den Namen der AdornmentLayer aus **KeyBindingTest** zu **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Behandeln der TYPECHAR-Befehl
Vor Visual Studio 2017 Version 15.6, die die einzige Möglichkeit zum Verarbeiten von Befehlen in einer Editor-Erweiterung implementiert wurde ein <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Befehlsfilter basiert. Visual Studio 2017 Version 15.6 eingeführt, einen modernen, vereinfachten Ansatz basierend auf den Handler für Editor-Befehl. In den nächsten beiden Abschnitten wird das Behandeln eines Befehls mit der sowohl die ältere und moderne Ansatz veranschaulicht.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definieren Sie den Befehlsfilter (vor Visual Studio 2017 Version 15.6)

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

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7.  Implementieren der `Exec()` Methode, sodass die It eine violette Box an die Ansicht Wenn ein Pluszeichen hinzugefügt (**+**) Zeichen eingegeben wird.

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Fügen Sie den Befehlsfilter (vor Visual Studio 2017 Version 15.6)
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

2.  Um der Textansichtsadapter zu erhalten, müssen Sie importieren die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.

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

4.  Die `AddCommandFilter` Handler ruft der Textansichtsadapter, und der Befehlsfilter hinzugefügt.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementieren Sie einen Befehlshandler (ab Visual Studio 2017 Version 15.6)

Aktualisieren Sie zunächst die Nuget-Verweise des Projekts, um auf den neuesten-Editor-API zu verweisen:

1. Mit der rechten Maustaste auf das Projekt, und wählen Sie **Nuget-Pakete verwalten**.

2. In **Nuget Package Manager**, wählen die **Updates** Registerkarte die **wählen Sie alle Pakete** Kontrollkästchen, und wählen Sie dann **Update**.

Die Befehlshandler ist eine Implementierung von <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, behandelt den Befehl durch Instanziieren des Zusatzelements ab.

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `KeyBindingCommandHandler`.

2. Fügen Sie die folgenden using-Anweisungen hinzu.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. Die Klasse, die mit dem Namen KeyBindingCommandHandler erben soll `ICommandHandler<TypeCharCommandArgs>`, und exportieren Sie es als <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Fügen Sie einen Anzeigenamen, der den Befehlshandler hinzu:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implementieren der `GetCommandState()` -Methode wie folgt. Da es sich bei diesen Befehlshandler Kern-Editor TYPECHAR-Befehl verarbeitet, können sie delegieren, aktivieren den Befehl aus, um die Kern-Editor.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementieren der `ExecuteCommand()` Methode, sodass die It eine violette Box an die Ansicht Wenn ein Pluszeichen hinzugefügt (**+**) Zeichen eingegeben wird.

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
   7. Kopieren Ebene-Definition von Zusatzelement *KeyBindingTestTextViewCreationListener.cs* -Datei in die *KeyBindingCommandHandler.cs* und löschen Sie  *KeyBindingTestTextViewCreationListener.cs* Datei:

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

## <a name="make-the-adornment-appear-on-every-line"></a>Stellen Sie das Zusatzelement in jeder Zeile angezeigt werden

Das ursprüngliche Zusatzelement angezeigt wird, für jedes enthaltene Zeichen "a" in eine Textdatei. Nun, dass wir den Code zum Hinzufügen des Zusatzelements in Reaktion auf geändert haben die **+** Zeichen, das Zusatzelement nur in der Zeile hinzugefügt, in denen die **+** Zeichen eingegeben wird. Ändern wir den Code des Zusatzelements, damit das Zusatzelement noch einmal auf angezeigt wird jedes "a".

In der *KeyBindingTest.cs* Datei die `CreateVisuals()` Methode, um alle Zeilen in der Ansicht, um das Zeichen "a" ergänzen durchlaufen.

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

1.  Erstellen Sie die KeyBindingTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.

2.  Erstellen Sie oder öffnen Sie eine Textdatei. Geben Sie einige Wörter, die mit dem Zeichen "a", und geben Sie dann **+** an einer beliebigen Stelle in der Textansicht.

     Eine violette Quadrat sollte auf jedem Zeichen "a" in der Datei angezeigt werden.
