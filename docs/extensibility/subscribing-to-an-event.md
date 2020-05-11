---
title: Abonnieren eines Ereignisses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699688"
---
# <a name="subscribing-to-an-event"></a>Abonnieren eines Ereignisses
In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie ein Toolfenster erstellen, das auf Ereignisse in einer laufenden Dokumenttabelle (RDT) reagiert. Ein Toolfenster hostet ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>Benutzersteuerelement, das implementiert. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet die Schnittstelle mit den Ereignissen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Abonnieren von RDT-Ereignissen

#### <a name="to-create-an-extension-with-a-tool-window"></a>So erstellen Sie eine Erweiterung mit einem Werkzeugfenster

1. Erstellen Sie ein Projekt mit dem Namen **RDTExplorer** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Vorlagenvorlage für das Toolfenster mit dem Namen **RDTExplorerWindow**hinzu.

     Weitere Informationen zum Erstellen einer Erweiterung mit einem Toolfenster finden Sie unter [Erstellen einer Erweiterung mit einem Werkzeugfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>So abonnieren Sie RDT-Ereignisse

1. Öffnen Sie die Datei RDTExplorerWindowControl.xaml, und löschen Sie die Schaltfläche mit dem Namen `button1`. Fügen <xref:System.Windows.Forms.ListBox> Sie ein Steuerelement hinzu, und akzeptieren Sie den Standardnamen. Das Grid-Element sollte wie folgt aussehen:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Öffnen Sie die RDTExplorerWindow.cs Datei in der Codeansicht. Fügen Sie dem Anfang der Datei die folgenden Anweisungen mithilfe von Direktiven hinzu.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Ändern `RDTExplorerWindow` Sie die Klasse so, dass sie <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> nicht nur von <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> der Klasse ableitet, sondern auch die Schnittstelle implementiert.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementieren Sie die Schnittstelle. Platzieren Sie den Cursor auf dem Namen IVsRunningDocTableEvents. Sie sollten eine Glühbirne am linken Rand sehen. Klicken Sie auf den Abwärtspfeil rechts neben der Glühbirne und wählen Sie **Schnittstelle implementieren**aus.

5. Ersetzen Sie in jeder Methode `throw new NotImplementedException();` in der Schnittstelle die Zeile durch die folgende:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Fügen Sie der RDTExplorerWindow-Klasse ein Cookiefeld hinzu.

    ```csharp
    private uint rdtCookie;
    ```

     Dies enthält das Cookie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> das von der Methode zurückgegeben wird.

7. Überschreiben Sie die Initialize()-Methode von RDTExplorerWindow, um sich für RDT-Ereignisse zu registrieren. Sie sollten immer Dienste in der Initialize()-Methode von ToolWindowPane abrufen, nicht im Konstruktor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Der <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Dienst wird aufgerufen, um eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle zu erhalten. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet RDT-Ereignisse mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>einem Objekt, das in diesem Fall ein RDTExplorer-Objekt implementiert.

8. Aktualisieren Sie die Dispose()-Methode von RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Methode löscht die `RDTExplorer` Verbindung zwischen und rdT-Ereignisbenachrichtigung.

9. Fügen Sie die folgende Zeile <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> dem Text `return` des Handlers kurz vor der Anweisung hinzu.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Fügen Sie dem Textkörper <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> des Handlers und anderen Ereignissen, die im Listenfeld angezeigt werden sollen, eine ähnliche Zeile hinzu.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

12. Öffnen Sie das **RDTExplorerWindow** (**Ansicht / Andere Windows / RDTExplorerWindow**).

     Das **RDTExplorerWindow-Fenster** wird mit einer leeren Ereignisliste geöffnet.

13. Öffnen oder erstellen Sie eine Lösung.

     Wenn `OnBeforeLastDocument` `OnAfterFirstDocument` Ereignisse ausgelöst werden, wird die Benachrichtigung über jedes Ereignis in der Ereignisliste angezeigt.
