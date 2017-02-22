---
title: "Abonnieren eines Ereignisses | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ausgeführten Dokumenttabelle (RDT), reagieren auf Ereignisse"
  - "ausgeführten Dokumenttabelle (RDT), Abonnieren von Ereignissen"
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# Abonnieren eines Ereignisses
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird erläutert, wie ein Toolfenster erstellen, die auf Ereignisse in einem ausgeführten Dokumenttabelle \(RDT\) reagiert wird. Ein Toolfenster enthält ein Benutzersteuerelement, implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet die Schnittstelle mit der Ereignisse.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Abonnieren von Ereignissen RDT  
  
#### So erstellen Sie eine Erweiterung mit einem Toolfenster  
  
1.  Erstellen Sie ein Projekt mit dem Namen **RDTExplorer** mithilfe der VSIX\-Projektvorlage, und fügen Sie eine benutzerdefiniertes Tool Fenster Elementvorlage, die mit dem Namen **RDTExplorerWindow**.  
  
     Weitere Informationen zum Erstellen von einer Erweiterungs mit einem Toolfenster, finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### RDT Ereignisse abonnieren  
  
1.  Öffnen Sie die Datei RDTExplorerWindowControl.xaml, und löschen Sie die Schaltfläche mit dem Namen `button1`. Hinzufügen einer <xref:System.Windows.Forms.ListBox> steuern und den Standardnamen übernehmen. Das Grid\-Element sollte wie folgt aussehen:  
  
    ```xml  
    <Grid> <StackPanel Orientation="Vertical" Margin="-10,10,10,0"> <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock> <ListBox x:Name="listBox" Height="100" /> </StackPanel> </Grid>  
    ```  
  
2.  Öffnen Sie die Datei RDTExplorerWindow.cs, in der Codeansicht. Fügen Sie die folgende using\-Anweisungen am Anfang der Datei.  
  
    ```c#  
    using Microsoft.VisualStudio; using Microsoft.VisualStudio.Shell; using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Ändern der `RDTExplorerWindow` Klasse daher, zusätzlich zum Ableiten von der <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> \-Klasse implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> Schnittstelle.  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents {. . .}  
    ```  
  
4.  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Die\-Schnittstelle implementiert. Platzieren Sie den Cursor auf den Namen des IVsRunningDocTableEvents. Sie sollten eine Glühbirne am linken Rand angezeigt. Klicken Sie auf den Pfeil nach unten neben der Glühbirne, und wählen Sie **Schnittstelle implementieren**.  
  
5.  Ersetzen Sie in jeder Methode in der Schnittstelle, die Zeile `throw new NotImplementedException();` mit diesem:  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  Fügen Sie ein Cookiefeld der RDTExplorerWindow\-Klasse.  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     Dies gilt, dass das Cookie, das von zurückgegebene die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode.  
  
7.  Überschreiben Sie die RDTExplorerWindow Initialize\(\)\-Methode RDT Ereignisse registrieren. Sie sollten immer in der ToolWindowPane Initialize\(\)\-Methode nicht im Konstruktor Dienste erhalten.  
  
    ```c#  
    protected override void Initialize() { IVsRunningDocumentTable rdt = (IVsRunningDocumentTable) this.GetService(typeof(SVsRunningDocumentTable)); rdt.AdviseRunningDocTableEvents(this, out rdtCookie); }  
    ```  
  
     Die <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Service wird aufgerufen, um das Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet RDT Ereignisse mit einem Objekt, implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, in diesem Fall ein RDTExplorer\-Objekt.  
  
8.  Aktualisieren Sie die RDTExplorerWindow Dispose\(\)\-Methode.  
  
    ```c#  
    protected override void Dispose(bool disposing) { // Release the RDT cookie. IVsRunningDocumentTable rdt = (IVsRunningDocumentTable) Package.GetGlobalService(typeof(SVsRunningDocumentTable)); rdt.UnadviseRunningDocTableEvents(rdtCookie); base.Dispose(disposing); }  
    ```  
  
     Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> \-Methode löscht die Verbindung zwischen `RDTExplorer` und RDT Benachrichtigung.  
  
9. Fügen Sie die folgende Zeile in den Hauptteil der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> Ereignishandler kurz vor der `return` Anweisung.  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining) { ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock"); return VSConstants.S_OK; }  
    ```  
  
10. Fügen Sie eine ähnliche Zeile in den Hauptteil der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> Ereignishandler und andere Ereignisse, die Sie im Listenfeld anzeigen möchten.  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining) { ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock"); return VSConstants.S_OK; }  
    ```  
  
11. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
12. Öffnen Sie die **RDTExplorerWindow** \(**Anzeigen \/ andere Fenster \/ RDTExplorerWindow**\).  
  
     Die **RDTExplorerWindow** mit einer leeren Liste wird geöffnet.  
  
13. Öffnen Sie oder erstellen Sie eine Lösung.  
  
     Als `OnBeforeLastDocument` und `OnAfterFirstDocument` Ereignisse werden ausgelöst, benachrichtigt, wenn jedes Ereignis im Ereignisprotokoll Liste angezeigt.