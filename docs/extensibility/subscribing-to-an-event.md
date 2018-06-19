---
title: Abonnieren eines Ereignisses | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41ed19cb31924e90ef9326aad5c8cad117996793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141902"
---
# <a name="subscribing-to-an-event"></a>Abonnieren eines Ereignisses
In dieser exemplarischen Vorgehensweise wird erläutert, wie ein Toolfenster erstellen, die mit Ereignissen in eine Dokumenttabelle der ausgeführten (RDT) reagiert wird. Ein Toolfenster hostet ein Benutzersteuerelement, das implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet die Schnittstelle mit den Ereignissen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Abonnieren von Ereignissen RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>So erstellen Sie eine Erweiterung mit einem Toolfenster  
  
1.  Erstellen Sie ein Projekt mit dem Namen **RDTExplorer** die VSIX-Vorlage, und fügen Sie eine Elementvorlage für benutzerdefiniertes Tool-Fenster mit dem Namen **RDTExplorerWindow**.  
  
     Weitere Informationen zum Erstellen von Erweiterung mit einem Toolfenster, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT Ereignisse abonnieren  
  
1.  Öffnen Sie die Datei RDTExplorerWindowControl.xaml und die Schaltfläche mit dem Namen "löschen" `button1`. Hinzufügen einer <xref:System.Windows.Forms.ListBox> steuern und übernehmen Sie den Standardnamen. Das Grid-Element sollte wie folgt aussehen:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Öffnen Sie die Datei RDTExplorerWindow.cs, in der Codeansicht. Fügen Sie die folgenden using-Anweisungen am Anfang der Datei.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Ändern der `RDTExplorerWindow` -Klasse so, zusätzlich zum Ableiten von der <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> -Klasse implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> Schnittstelle.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Implementieren Sie die Schnittstelle. Platzieren Sie den Cursor auf den Namen des IVsRunningDocTableEvents an. Es sollte eine Glühbirne am linken Rand angezeigt. Klicken Sie auf den Pfeil nach unten rechts neben die Glühbirne, und wählen Sie **Schnittstelle implementieren**.  
  
5.  Ersetzen Sie in jeder Methode in der Schnittstelle, die Zeile `throw new NotImplementedException();` mit diesem:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Fügen Sie ein Cookiefeld der RDTExplorerWindow-Klasse.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Dies ist das Cookie an, die von zurückgegeben wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode.  
  
7.  Überschreiben Sie die RDTExplorerWindow Initialize()-Methode für RDT Ereignisse registrieren. Sie sollten die ToolWindowPane Initialize()-Methode nicht im Konstruktor immer Dienste abrufen.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     Die <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Service wird aufgerufen, um das Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> verbindet RDT Ereignisse auf ein Objekt, das implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, in diesem Fall ein RDTExplorer-Objekt.  
  
8.  Aktualisieren Sie die RDTExplorerWindow Dispose()-Methode.  
  
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
  
     Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> -Methode löscht die Verbindung zwischen `RDTExplorer` und RDT ereignisbenachrichtigung.  
  
9. Fügen Sie die folgende Zeile in den Text der der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> Ereignishandler kurz vor dem Ausführen der `return` Anweisung.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Fügen Sie eine ähnliche Zeile in den Text der der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> Ereignishandler und andere Ereignisse, die Sie im Listenfeld anzeigen möchten.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
12. Öffnen der **RDTExplorerWindow** (**Ansicht / anderen Fenstern / RDTExplorerWindow**).  
  
     Die **RDTExplorerWindow** mit einer leeren Liste wird geöffnet.  
  
13. Öffnen Sie oder erstellen Sie eine Projektmappe.  
  
     Als `OnBeforeLastDocument` und `OnAfterFirstDocument` Ereignisse werden ausgelöst, die Benachrichtigung jedes Ereignisses im Ereignisprotokoll Liste angezeigt.