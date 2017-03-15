---
title: "Dokumenttabelle der ausgef&#252;hrten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sperren"
  - "ausgeführten Dokumenttabelle (RDT), IVsDocumentLockHolder-Schnittstelle"
  - "ausgeführten Dokumenttabelle (RDT)"
  - "ausgeführten Dokumenttabelle (RDT), Sperren bearbeiten"
  - "Dokument-Datenobjekte, die unter der Document-Tabelle"
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Dokumenttabelle der ausgef&#252;hrten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die IDE verwaltet die Liste aller geöffneten Dokumente in einer internen Struktur die ausgeführten Dokumenttabelle \(RDT\) aufgerufen. Diese Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob diese Dokumente derzeit bearbeitet wird. Jedes Element, das beibehalten wird, einschließlich der Dateien in einem Projekt oder der Hauptprojektdatei \(z. B. eine VCXPROJ\-Datei\) ist ein Dokument.  
  
## Elemente der Dokumenttabelle ausgeführt wird  
 Die Dokumenttabelle der ausgeführten enthält die folgenden Einträge.  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Dokumentmoniker|Eine Zeichenfolge, die das Dokumentobjekt eindeutig identifiziert. Dies wäre der vollständige Dateipfad für ein Projektsystem, die Dateien \(z. B. C:\\MyProject\\MyFile\) verwaltet. Diese Zeichenfolge dient auch für Projekte, die im Speicher als Dateisysteme, z. B. gespeicherte Prozeduren in einer Datenbank gespeichert. In diesem Fall kann das Projektsystem eine eindeutige Zeichenfolge erfinden, die es erkennt und möglicherweise analysieren, um zu bestimmen, wie Sie das Dokument speichern kann.|  
|Besitzer der Hierarchie|Hierarchy\-Objekt, das das Dokument besitzt, dargestellt durch eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle.|  
|Element\-ID|Bezeichner für ein bestimmtes Element in der Hierarchie. Dieser Wert ist für alle Dokumente in der Hierarchie, die im Besitz dieses Dokuments ist eindeutig, aber dieser Wert wird nicht unbedingt für verschiedene Hierarchien eindeutig sein.|  
|Dokument\-Datenobjekt|In jedem Fall ist dies ein `IUnknown`<br /><br /> \-Objekts. Die IDE erfordert keine bestimmte Schnittstelle über die `IUnknown` Schnittstelle für einen benutzerdefinierten Editor\-Dokument\-Datenobjekt. Für einen standard\-Editor, jedoch Implementierung des Editors die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle ist erforderlich, um die Datei\-Persistenz\-Aufrufe aus dem Projekt zu verarbeiten. Weitere Informationen finden Sie unter [Ein standardisiertes Dokument speichern](../../extensibility/internals/saving-a-standard-document.md).|  
|Flags|Flags, die steuern, ob das Dokument gespeichert wird, erfolgt eine Sperre lesen oder bearbeiten usw., können angegeben werden, wenn die RDT Einträge hinzugefügt werden. Weitere Informationen finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Enumeration.|  
|Bearbeiten Sie die Anzahl der Sperren|Die Anzahl der Sperren bearbeiten. Eine Sperre bearbeiten gibt für ein Text\-Editor das Dokument zur Bearbeitung zu öffnen. Wenn 0 \(null\) die Anzahl der Sperren bearbeiten einführt, wird der Benutzer aufgefordert, das Dokument zu speichern, wenn es geändert wurde. Z. B. bei jedem Öffnen ein Dokuments in einem Editor mithilfe der **Neues Fenster** Befehl, eine Sperre bearbeiten für das Dokument in der RDT hinzugefügt wird. Damit eine Sperre bearbeiten festgelegt werden kann muss das Dokument bilden eine Hierarchie oder Element\-ID|  
|Lesen der Anzahl von Sperren|Anzahl der gelesenen sperren. Eine Lesesperre gibt an, dass das Dokument über einen Mechanismus wie z. B. einen Assistenten gelesen wird. Eine Lesesperre enthält ein Dokument in der RDT aktiv, während der, der angibt, dass das Dokument bearbeitet werden kann. Sie können eine Lesesperre festlegen, auch wenn das Dokument nicht über eine Hierarchie verfügen oder\-ID Element Dieses Feature können Sie zum Öffnen eines Dokuments im Speicher, und geben ihn in die RDT ohne das Dokument jeder Hierarchie gehört. Diese Funktion wird nur selten verwendet.|  
|Inhaber der Sperre|Eine Instanz einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Der Inhaber der Sperre wird durch Features wie Assistenten implementiert, die Dokumente außerhalb eines Editors geöffnet und bearbeitet. Inhaber der Sperre können Sie die Funktion eine Sperre bearbeiten hinzufügen, auf das Dokument, um zu verhindern, dass das Dokument geschlossen, während es noch bearbeitet wird. Bearbeiten Sie in der Regel Sperren werden nur vom Dokumentfenster \(d. h. Editoren\) hinzugefügt.|  
  
 Jeder Eintrag in der RDT hat eine eindeutige Hierarchie oder die Element\-ID zugeordnet, die im Allgemeinen auf einen Knoten im Projekt entspricht. Eine Hierarchie gehören in der Regel alle Dokumente, die für die Bearbeitung verfügbar. Einträge in der RDT steuern, welches Projekt oder, genauer – die Hierarchie derzeit besitzt das Datenobjekt Dokument bearbeitet wird. Anhand der Informationen in der RDT, kann die IDE ein Dokument verhindern gleichzeitig von mehr als ein Projekt geöffnet wird.  
  
 Die Hierarchie auch steuert die Dauerhaftigkeit der Daten und verwendet die Informationen in den RDT aktualisieren die **Speichern** und **Speichern** Dialogfelder. Wenn Benutzer ein Dokument ändern, und wählen Sie dann die **Beenden** Befehl die **Datei** im Menü die IDE aufgefordert, mit der **Speichern** Dialogfeld die Anzeige aller Projekte und Projektelemente, die gerade geändert werden. Dadurch können Benutzer wählen, zu welcher der Dokumente zu speichern. Die Liste der Dokumente zu speichern \(d. h. diese Dokumente, die geändert wurden\) aus der RDT generiert wird. Alle Elemente, die Sie erwarten, sehen in der **Speichern** Dialogfeld beim Beenden der Anwendung sollte die RDT Datensätze enthalten. Die RDT koordiniert, welche Dokumente gespeichert werden, und gibt an, ob der Benutzer aufgefordert wird, über einen Vorgang mit den Werten, die im Flags\-Eintrag für jedes Dokument angegeben. Weitere Informationen zu den RDT Flags finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Enumeration.  
  
## Bearbeiten von Sperren und Lesesperren  
 Bearbeiten von Sperren und Lesesperren befinden sich in der RDT. Der Dokument\-Fenster\-inkrementiert und dekrementiert die Bearbeitung gesperrt. Daher, wenn ein Benutzer ein neuen Dokumentfenster geöffnet wird, die bearbeiten Sperrenanzahl Schritten von einem. Wenn die Anzahl der Sperren bearbeiten 0 \(null\) erreicht, wird die Hierarchie signalisiert, erhalten bleiben, oder speichern Sie die Daten für das zugeordnete Dokument. Die Hierarchie kann dann die Daten in keiner Weise beibehalten werden, als eine Datei oder ein Element in einem Repository einschließlich beibehalten. Können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> \-Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle hinzufügen bearbeiten sperren und sperren, und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode, um diese Sperren zu entfernen.  
  
 In der Regel bei der Instanziierung Dokumentfenster für einen Editor hinzugefügt Fensterrahmen in automatisch eine Sperre bearbeiten für das Dokument die RDT. Wenn Sie eine benutzerdefinierte Ansicht eines Dokuments erstellen, die verwendet jedoch keinem standard Dokumentfenster \(d. h. wird nicht implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle\), müssen Sie Ihre eigene Sperre bearbeiten festgelegt. Beispielsweise wird in einem Assistenten wird ein Dokument bearbeiten, ohne in einem Editor geöffnet wird. Damit Dokumentsperren von Assistenten und ähnliche Entitäten geöffnet werden kann, müssen diese Entitäten implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Um Ihr Dokument sperren Inhaber zu registrieren, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> \-Methode, und übergeben Sie Ihr <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Implementierung. Auf diese Weise wird die RDT der Inhaber der Sperre Dokument hinzugefügt. Ein weiteres Szenario für ein Dokument sperren Inhaber implementieren ist, wenn Sie ein Dokument über eine spezielle Toolfenster öffnen. In diesem Fall können Sie nicht das Toolfenster, schließen Sie das Dokument haben. Durch die Registrierung als Halter Dokument Sperren in der RDT die IDE kann jedoch aufrufen, die Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> Methode, um ein Schließen des Dokuments aufgefordert.  
  
## Andere Verwendungen der Document\-Tabelle ausgeführt wird  
 Andere Entitäten in der IDE verwenden die RDT zum Abrufen von Informationen zu Dokumenten. Beispielsweise verwendet der Quell\-Manager die RDT anzuweisen, das System ein Dokument im Editor laden, nachdem sie die neueste Version der Datei abruft. Dazu sucht der Datenquellen\-Manager die Dateien in der RDT, um festzustellen, ob diese geöffnet sind. Wenn sie der Datenquellen\-Manager zunächst überprüft, ob die Hierarchie implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. Wenn das Projekt nicht implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> \-Methode, und klicken Sie dann auf die Quelle steuern überprüft eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Methode direkt im Dokument\-Datenobjekt.  
  
 Die IDE verwendet auch die RDT um zu diesem \(in den Vordergrund bringen\) einem geöffneten Dokument, wenn ein Benutzer das Dokument anfordert. Weitere Informationen finden Sie unter [Anzeigen von Dateien mit dem Befehl Datei öffnen](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Bestimmt, ob eine Datei in die RDT geöffnet ist, führen Sie eine der folgenden.  
  
-   Die Abfrage für den dokumentmoniker \(d. h. der Pfad vollständiges Dokument\), um festzustellen, ob das Element geöffnet ist.  
  
-   Verwenden Sie die Hierarchie oder Element\-ID, um Fragen Sie das Projektsystem für den vollständigen Pfad, und suchen das Element in der RDT.  
  
## Siehe auch  
 [RDT\_ReadLock Verwendung](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistenz und der Document\-Tabelle ausgeführt wird](../../extensibility/internals/persistence-and-the-running-document-table.md)