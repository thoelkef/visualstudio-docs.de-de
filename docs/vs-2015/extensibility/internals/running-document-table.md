---
title: Document-Tabelle mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd7b8cd44c72ea058f71575bdd1774efafa86731
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746303"
---
# <a name="running-document-table"></a>Aktive Dokumenttabelle
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die IDE verwaltet die Liste aller aktuell geöffneten Dokumente in einer internen Struktur der ausgeführten Dokumententabelle (RDT) aufgerufen. Diese Liste enthält alle geöffneten Dokumente im Arbeitsspeicher, unabhängig davon, ob diese Dokumente derzeit bearbeitet wird. Ein Dokument ist ein Element, das gespeichert wird, einschließlich der Dateien in einem Projekt oder der Hauptprojektdatei (z. B. eine VCXPROJ-Datei).  
  
## <a name="elements-of-the-running-document-table"></a>Elemente der die aktive Dokumenttabelle  
 Der ausgeführten Dokumententabelle enthält die folgenden Einträge.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Dokumentenmoniker|Eine Zeichenfolge, die das dokumentendatenobjekt eindeutig identifiziert. Dies wäre der absolute Dateipfad für ein Projektsystem, die Dateien (z. B. C:\MyProject\MyFile) verwaltet werden. Diese Zeichenfolge dient auch für Projekte, die in anderen speichern als Dateisysteme, z. B. gespeicherte Prozeduren in einer Datenbank gespeichert. In diesem Fall kann das Projektsystem eine eindeutige Zeichenfolge erfinden, die sie erkennen und möglicherweise analysieren, um zu bestimmen, wie Sie das Dokument speichern kann.|  
|Hierarchie-Besitzer|Das Hierarchy-Objekt, das das Dokument besitzt, dargestellt durch ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle.|  
|Element-ID|Der Elementbezeichner für ein bestimmtes Element innerhalb der Hierarchie. Dieser Wert ist für alle Dokumente in der Hierarchie, die Besitzer dieses Dokument ist, eindeutig, aber dieser Wert ist nicht zwingend über verschiedene Hierarchien hinweg eindeutig sein.|  
|Dokumentendatenobjekt|In jedem Fall ist dies ein `IUnknown`<br /><br /> -Objekts. Die IDE erfordert keine bestimmte Schnittstelle über keine der `IUnknown` Schnittstelle für einen benutzerdefinierten Editor-Dokument-Datenobjekt. Für eine standard-Editor jedoch Implementierung des Editors die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle ist erforderlich, um die Datei-Persistenz-Aufrufe aus dem Projekt zu verarbeiten. Weitere Informationen finden Sie unter [Speichern eines Standarddokuments](../../extensibility/internals/saving-a-standard-document.md).|  
|Flags|Flags, die steuern, ob eine Lese- oder Bearbeitungssperre angewendet wird, ob das Dokument gespeichert wird, und So weiter, können angegeben werden, wenn der RDT Einträge hinzugefügt werden. Weitere Informationen finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>-Enumeration.|  
|Bearbeiten Sie die Anzahl der Sperren|Die Anzahl der bearbeitungssperren. Eine Bearbeitungssperre gibt an, für ein Text-Editor das Dokument zur Bearbeitung zu öffnen. Wenn die Anzahl der bearbeitungssperren 0 (null) wechselt, wird der Benutzer zum Speichern des Dokuments, aufgefordert, wenn es geändert wurde. Beispielsweise jedes Mal, wenn Sie ein Dokument in einem Editor mit öffnen die **neues Fenster** -Befehls wird eine Bearbeitungssperre für dieses Dokument im RDT hinzugefügt wird. Damit eine Bearbeitungssperre festgelegt werden kann muss das Dokument über eine Hierarchie verfügen oder Element-ID|  
|Anzahl von Lesevorgängen Sperren|Anzahl der Lesesperren. Eine Lesesperre gibt an, dass das Dokument über einen Mechanismus, z. B. ein Assistenten gelesen wird. Eine Lesesperre enthält ein Dokument in der RDT aktiv und gibt an, dass das Dokument kann nicht bearbeitet werden. Sie können eine Lesesperre festlegen, auch wenn das Dokument nicht über eine Hierarchie verfügen oder-ID Element Dieses Feature können Sie zum Öffnen eines Dokuments im Arbeitsspeicher, und geben ihn in der RDT ohne das Dokument, das jeder Hierarchie gehört. Diese Funktion wird nur selten verwendet.|  
|Besitzer der Sperre|Eine Instanz von einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Der Inhaber der Sperre wird von Features wie z. B. Assistenten implementiert, die öffnen und Bearbeiten von Dokumenten außerhalb eines Editors. Ein Sperre Inhaber ermöglicht die Funktion, um eine Bearbeitungssperre hinzuzufügen, auf das Dokument, um zu verhindern, dass das Dokument geschlossen wird, während es immer noch bearbeitet wird. Bearbeiten Sie in der Regel Sperren werden nur durch Dokumentfenster (d. h. Editoren) hinzugefügt.|  
  
 Jeder Eintrag in der RDT ist eine eindeutige Hierarchie oder die Element-ID zugeordnet, die in der Regel auf einen Knoten im Projekt entspricht. Alle Dokumente, die zur Bearbeitung verfügbar, werden in der Regel im Besitz einer Hierarchie. Einträge in der RDT steuern, welches Projekt, oder, genauer: die Hierarchie derzeit besitzt das dokumentendatenobjekt, das bearbeitet wird. Mit den Informationen in der RDT kann die IDE ein Dokuments verhindern gleichzeitig von mehr als ein Projekt geöffnet wird.  
  
 Die Hierarchie auch steuert die Dauerhaftigkeit der Daten und verwendet die Informationen in der RDT zum Aktualisieren der **speichern** und **speichern** Dialogfelder. Beim Benutzer ein Dokument zu ändern, und wählen Sie dann die **beenden** Befehl die **Datei** im Menü die IDE werden aufgefordert, diese mit der **Save Changes** Dialogfelds werden alle Projekte anzeigen und Projektelemente, die derzeit geändert werden. Dadurch können Benutzer wählen, welche die Dokumente speichern möchten. Die Liste der zu speichernden Dokumente (d. h. diese Dokumente, die Änderungen haben) aus dem RDT generiert wird. Alle Elemente, die Sie erwarten in dem **Save Changes** Dialogfeld beim Beenden der Anwendungs müssen Datensätze in der RDT. Der RDT koordiniert, welche Dokumente gespeichert werden, und gibt an, ob der Benutzer aufgefordert wird, über einen Vorgang mit den Werten in den Flags-Eintrag für jedes Dokument angegeben. Weitere Informationen zu den RDT-Flags finden Sie unter den <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Enumeration.  
  
## <a name="edit-locks-and-read-locks"></a>Bearbeitungssperren und Read-Sperren  
 Bearbeitungssperren und Lesesperren befinden sich in der RDT. Der Dokument-Fenster-inkrementiert bzw. dekrementiert die Bearbeitung gesperrt werden. Daher Wenn ein Benutzer ein neues Dokumentfenster geöffnet wird, die bearbeiten Sperrenanzahl inkrementiert um eins. Wenn die Anzahl der bearbeitungssperren 0 (null) erreicht, wird die Hierarchie angegeben, dass beibehalten oder speichern die Daten für das zugeordnete Dokument. Die Hierarchie kann dann die Daten in keiner Weise, einschließlich der persistenten Speicherung als eine Datei oder als ein Element in einem Repository persistent gespeichert werden. Können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> -Methode in der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle zum Hinzufügen von bearbeitungssperren und Lesen von Sperren, und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode zum Entfernen dieser Sperren.  
  
 In der Regel, wenn das Dokumentfenster für einen Editor instanziiert wird, fügt der Fensterrahmen automatisch eine Bearbeitungssperre für das Dokument im RDT. Wenn Sie eine benutzerdefinierte Ansicht eines Dokuments erstellen, die verwendet jedoch keiner standard-Dokumentfenster (d. h., er implementiert nicht die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle), müssen Sie Ihre eigenen Bearbeitungssperre festgelegt. Beispielsweise wird in einem Assistenten, ein Dokument bearbeitet, ohne die in einem Editor geöffnet wird. Damit für Dokumentsperren von Assistenten und ähnliche Entitäten geöffnet werden kann, müssen diese Entitäten implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Um Ihre dokumentensperrenhalter zu registrieren, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> -Methode, und übergeben Ihr <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Implementierung. Auf diese Weise wird der RDT Ihre dokumentensperrenhalter hinzugefügt. Ein weiteres Szenario für die Implementierung eines dokumentensperrenhalter ist, wenn Sie ein Dokument über eine spezielle Toolfenster öffnen. In diesem Fall können Sie nicht das Toolfenster schließen Sie das Dokument zu haben. Allerdings als einen dokumentensperrenhalter in der RDT registriert wird, die IDE kann aufrufen Ihrer Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> Methode, eine Schließen des Dokuments aufgefordert.  
  
## <a name="other-uses-of-the-running-document-table"></a>Andere verwendet die aktive Dokumenttabelle  
 Andere Entitäten in der IDE verwenden der RDT zum Abrufen von Informationen zu Dokumenten. Beispielsweise verwendet der Quell-Steuerungs-Manager der RDT, teilen Sie das System, laden ein Dokument im Editor aus, nachdem sie die neueste Version der Datei abruft. Zu diesem Zweck sucht die Dateien in der aktiven Dokumenttabelle, um festzustellen, ob diese geöffnet sind, der Source-Steuerungs-Manager. Wenn sie sind, wird der Source-Steuerungs-Manager zuerst überprüft, dass die Hierarchie implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode. Wenn das Projekt nicht implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> -Methode, und klicken Sie dann auf die Quelle steuern überprüft eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Methode für das dokumentendatenobjekt direkt.  
  
 Die IDE verwendet auch den RDT an diesem (Verschieben in den Vordergrund) einem geöffneten Dokument, wenn ein Benutzer das Dokument anfordert. Weitere Informationen finden Sie unter [Anzeigen von Dateien mithilfe des Befehls der geöffneten Datei](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Bestimmt, ob eine Datei geöffnet, in der RDT ist, führen Sie eine der folgenden.  
  
-   Abfrage für den dokumentmoniker (d. h. der vollständigen Dokuments-Pfad), um herauszufinden, ob das Element geöffnet ist.  
  
-   Verwenden Sie die Hierarchie oder das Element-ID, bitten Sie das Projektsystem für den Pfad des vollständigen Dokuments und suchen Sie dann das Element in der RDT.  
  
## <a name="see-also"></a>Siehe auch  
 [RDT_ReadLock-Verwendung](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistenz und die aktive Dokumenttabelle](../../extensibility/internals/persistence-and-the-running-document-table.md)

