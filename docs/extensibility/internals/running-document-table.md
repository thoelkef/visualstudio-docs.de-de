---
title: Document-Tabelle mit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 41a9fc5a2b364ecc0c9037980c3ef2804a6808d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="running-document-table"></a>Dokumenttabelle der ausgeführten
Die IDE verwaltet die Liste aller aktuell geöffneten Dokumente in einer internen Struktur die Dokumenttabelle der ausgeführten (RDT) aufgerufen. Diese Liste enthält alle geöffneten Dokumente im Arbeitsspeicher, unabhängig davon, ob diese Dokumente derzeit bearbeitet wird. Ein Dokument wird jeder, der beibehalten wird, einschließlich Dateien in einem Projekt oder die Haupt-Projektdatei (z. B. eine VCXPROJ-Datei).  
  
## <a name="elements-of-the-running-document-table"></a>Elemente der Document-Tabelle ausgeführt wird  
 Die Dokumenttabelle der ausgeführten enthält die folgenden Einträge.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Dokumentmoniker|Eine Zeichenfolge, die das dokumentdatenobjekt eindeutig identifiziert. Dies wäre der absolute Dateipfad für ein Projektsystem, das Dateien (z. B. C:\MyProject\MyFile) verwaltet. Diese Zeichenfolge dient auch für Projekte, die im Speicher als Dateisystemen, z. B. gespeicherte Prozeduren in einer Datenbank gespeichert. In diesem Fall kann das Projektsystem eine eindeutige Zeichenfolge auswählen, die sie erkennen und möglicherweise analysieren, um zu bestimmen, wie Sie das Dokument speichern kann.|  
|Besitzer der Hierarchie|Die Hierarchy-Objekt, das das Dokument besitzt, dargestellt durch eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle.|  
|Element-ID|Element-ID für ein bestimmtes Element innerhalb der Hierarchie. Dieser Wert ist für alle Dokumente in der Hierarchie, die Besitzer dieses Dokuments ist, eindeutig dieser Wert wird jedoch nicht garantiert für unterschiedliche Hierarchien eindeutig sein.|  
|Dokumentdatenobjekt|Die Mindestanforderung ist dies ein`IUnknown`<br /><br /> -Objekts. Die IDE erfordert eine bestimmte Schnittstelle hinter der `IUnknown` Schnittstelle für einen benutzerdefinierten Editor dokumentdatenobjekt. Allerdings für eine standard-Editors Implementierung des Editors die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle ist erforderlich, um die Datei Persistenz Aufrufe aus dem Projekt zu verarbeiten. Weitere Informationen finden Sie unter [Speichern eines Standarddokumentspeicher-](../../extensibility/internals/saving-a-standard-document.md).|  
|Flags|Flags, die steuern, ob eine Sperre lesen oder bearbeiten angewendet wird, ob das Dokument gespeichert wird, usw., können angegeben werden, wenn die RDT Einträge hinzugefügt werden. Weitere Informationen finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>-Enumeration.|  
|Bearbeiten Sie die Anzahl der Sperren|Die Anzahl der Sperren bearbeiten. Eine Sperre bearbeiten gibt an, dass einige Editor das Dokument zum Bearbeiten geöffnet hat. Wenn die Anzahl der Sperren bearbeiten auf Null geht, wird der Benutzer aufgefordert, das Dokument zu speichern, wenn er geändert wurde. Beispielsweise jedes Mal, wenn ein Dokument zu öffnen, in einem Editor mithilfe der **neues Fenster** Befehl, eine Sperre bearbeiten für das Dokument in der RDT hinzugefügt wird. Das Dokument muss in der Reihenfolge für eine Sperre bearbeiten festgelegt werden eine Hierarchie oder Element-ID|  
|Anzahl von Lesevorgängen Sperre|Anzahl der gelesenen sperren. Eine Lesesperre gibt an, dass das Dokument über einen Mechanismus, z. B. ein Assistenten gelesen wird. Eine Lesesperre besitzt ein Dokument in der RDT aktiv, während gibt an, dass das Dokument nicht bearbeitet werden kann. Sie können eine Lesesperre festlegen, auch wenn das Dokument nicht über eine Hierarchie verfügen oder-ID Element Diese Funktion können Sie ein Dokument im Arbeitsspeicher zu öffnen, und geben ihn in die RDT ohne das Dokument eine beliebige Hierarchie gehört. Diese Funktion wird nur selten verwendet.|  
|Lock-Inhaber|Eine Instanz von einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Der Inhaber der Sperre wird von Funktionen, z. B. Assistenten implementiert, die Dokumente außerhalb eines Editors geöffnet und bearbeitet. Ein Sperre Inhaber ermöglicht das Hinzufügen eine Sperre bearbeiten auf das Dokument, um zu verhindern, dass das Dokument geschlossen wird, während er noch bearbeitet wird. Bearbeiten Sie in der Regel Sperren werden nur vom Dokumentfenster (d. h. Editoren) hinzugefügt.|  
  
 Jeder Eintrag in der RDT hat eine eindeutige Hierarchie oder die Element-ID zugeordnet, die in der Regel auf einen Knoten im Projekt entspricht. Alle Dokumente, die zur Bearbeitung verfügbar sind in der Regel im Besitz einer Hierarchie. Einträge in der RDT steuern, welches Projekt oder – genauer – welche Hierarchie derzeit besitzt das dokumentdatenobjekt bearbeitet wird. Mit den Informationen in den RDT kann die IDE ein Dokument verhindern, dass zu einem Zeitpunkt von mehr als ein Projekt geöffnet wird.  
  
 Die Hierarchie auch steuert die Persistenz von Daten und verwendet die Informationen in den RDT zum Aktualisieren der **speichern** und **speichern unter** Dialogfelder. Wenn Benutzer ein Dokument ändern, und wählen Sie dann die **beenden** Befehl die **Datei** im Menü die IDE, diese mit der **Änderungen speichern** (Dialogfeld), die sie alle Projekte anzuzeigen und Projektelemente, die derzeit geändert werden. Dadurch können Benutzer auf welche dieser Dokumente zu speichern. Die Liste mit Dokumenten gespeichert (d. h. diese Dokumente, die Änderungen vorgenommen wurden) aus dem RDT generiert wird. Alle Elemente, die voraussichtlich in finden Sie unter der **Änderungen speichern** Dialogfeld beim Beenden der Anwendung sollte Datensätze verfügen, in der RDT. Die RDT koordiniert, welche Dokumente gespeichert werden, und gibt an, ob der Benutzer aufgefordert wird, über einen Vorgang mit den Werten in den Flags-Eintrag für jedes Dokument angegeben. Weitere Informationen zu den RDT Flags finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Enumeration.  
  
## <a name="edit-locks-and-read-locks"></a>Bearbeiten von Sperren und Lesesperren  
 Bearbeiten von Sperren und Lesesperren befinden sich in der RDT. Das Dokument Fenster inkrementiert und dekrementiert die Bearbeitung gesperrt werden. Daher, wenn ein Benutzer mit ein neuen Dokumentfenster geöffnet wird, die bearbeiten Sperrenanzahl inkrementiert um eins. Wenn die Anzahl der Sperren bearbeiten 0 (null) erreicht, wird die Hierarchie angegeben, dass beibehalten oder speichern Sie die Daten für das zugeordnete Dokument. Die Hierarchie kann dann die Daten in keiner Weise, einschließlich der persistenten Speicherung als eine Datei oder ein Element in einem Repository persistent gespeichert. Können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Benutzeroberfläche zum Hinzufügen von Sperren für bearbeiten und Lesesperren, und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode, um diese Sperren zu entfernen.  
  
 In der Regel wird bei der Instanziierung die Dokumentfenster für einen Editor fügt der Fensterrahmen automatisch eine Sperre bearbeiten für das Dokument in der RDT. Wenn Sie eine benutzerdefinierte Ansicht eines Dokuments erstellen, die verwendet jedoch keinem standard Dokumentfenster (d. h. er implementiert nicht die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle), müssen Sie Ihre eigene bearbeiten Sperre festgelegt. Beispielsweise wird in einem Assistenten wird ein Dokument bearbeitet, ohne in einem Editor geöffnet wird. Damit Dokument Sperren von Assistenten und ähnliche Entitäten geöffnet werden kann, müssen diese Entitäten implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Rufen Sie Informationen zum Registrieren Ihrer Dokument Sperre Inhaber der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> -Methode, und übergeben Ihr <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Implementierung. Auf diese Weise wird Ihr Dokument Sperre Inhaber der RDT hinzugefügt. Ein weiteres Szenario für die Implementierung von eines Dokument Sperre Inhabers ist, wenn Sie ein Dokument über eine spezielle Toolfenster zu öffnen. In diesem Fall können Sie nicht das Toolfenster, schließen Sie das Dokument haben. Allerdings als ein Dokument Inhaber der Sperre in der RDT registriert, die IDE kann aufrufen Ihrer Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> Methode, um ein Schließen des Dokuments aufgefordert.  
  
## <a name="other-uses-of-the-running-document-table"></a>Weitere Verwendungsmöglichkeiten der Document-Tabelle ausgeführt wird  
 Andere Entitäten in der IDE verwenden die RDT zum Abrufen von Informationen zu Dokumenten an. Beispielsweise verwendet der Quell-Steuerungs-Manager die RDT anzuweisen, das System, ein Dokument im Editor erneut zu laden, nachdem sie die neueste Version der Datei abruft. Zu diesem Zweck sucht der Quell-Steuerungs-Manager die Dateien in der RDT, um festzustellen, ob diese geöffnet sind. Wenn sie die Quell-Steuerungsmanager prüft zunächst, dass die Hierarchie implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. Wenn das Projekt nicht implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> -Methode, und klicken Sie dann auf die Quelle steuern Manager sucht eine Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> -Methode für das dokumentdatenobjekt direkt.  
  
 Die IDE verwendet auch die RDT um zu diesem (in den Vordergrund bringen) einem geöffneten Dokument, wenn ein Benutzer das Dokument anfordert. Weitere Informationen finden Sie unter [Anzeigen von Dateien mithilfe des Befehls der geöffneten Datei](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Um zu bestimmen, ob eine Datei in die RDT geöffnet ist, führen Sie einen der folgenden.  
  
-   Abfrage für den dokumentmoniker (d. h. der vollständigen Dokuments-Pfad), um festzustellen, ob das Element geöffnet ist.  
  
-   Verwenden Sie die Hierarchie oder ein Element-ID, um das Projektsystem die vollständige Dokumentpfad angefordert und suchen Sie das Element oben in der RDT.  
  
## <a name="see-also"></a>Siehe auch  
 [RDT_ReadLock Verwendung](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistenz und die aktive Dokumenttabelle](../../extensibility/internals/persistence-and-the-running-document-table.md)