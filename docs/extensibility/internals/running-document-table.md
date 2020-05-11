---
title: Ausführen der Dokumenttabelle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705568"
---
# <a name="running-document-table"></a>Aktive Dokumenttabelle
Die IDE verwaltet die Liste aller derzeit geöffneten Dokumente in einer internen Struktur, die als laufende Dokumenttabelle (RDT) bezeichnet wird. Diese Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob diese Dokumente gerade bearbeitet werden. Ein Dokument ist ein beliebiges Element, das beibehalten wird, einschließlich Dateien in einem Projekt oder der Hauptprojektdatei (z. B. eine .vcxproj-Datei).

## <a name="elements-of-the-running-document-table"></a>Elemente der Tabelle "Laufende sernende Dokument"
 Die laufende Dokumenttabelle enthält die folgenden Einträge.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Dokumentmoniker|Eine Zeichenfolge, die das Dokumentdatenobjekt eindeutig identifiziert. Dies wäre der absolute Dateipfad für ein Projektsystem, das Dateien verwaltet (z. B. C:-MyProject-MyFile). Diese Zeichenfolge wird auch für Projekte verwendet, die in anderen Speichern als Dateisystemen gespeichert werden, z. B. gespeicherte Prozeduren in einer Datenbank. In diesem Fall kann das Projektsystem eine eindeutige Zeichenfolge erfinden, die es erkennen und möglicherweise analysieren kann, um zu bestimmen, wie das Dokument gespeichert werden soll.|
|Hierarchiebesitzer|Das Hierarchieobjekt, dem das Dokument gehört, wie es durch eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle dargestellt wird.|
|Artikel-ID|Elementbezeichner für ein bestimmtes Element innerhalb der Hierarchie. Dieser Wert ist unter allen Dokumenten in der Hierarchie, die dieses Dokument besitzt, eindeutig, aber dieser Wert ist nicht garantiert eindeutig in verschiedenen Hierarchien.|
|Dokumentdatenobjekt|Zumindest ist dies ein`IUnknown`<br /><br /> -Objekts. Die IDE erfordert keine bestimmte `IUnknown` Schnittstelle über die Schnittstelle hinaus für das Dokumentdatenobjekt eines benutzerdefinierten Editors. Für einen Standardeditor ist jedoch die Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> der Schnittstelle durch den Editor erforderlich, um Dateipersistenzaufrufe aus dem Projekt zu verarbeiten. Weitere Informationen finden Sie unter [Speichern eines Standarddokuments](../../extensibility/internals/saving-a-standard-document.md).|
|Flags|Flags, die steuern, ob das Dokument gespeichert wird, ob eine Lese- oder Bearbeitungssperre angewendet wird usw., können angegeben werden, wenn Einträge zur RDT hinzugefügt werden. Weitere Informationen finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>-Enumeration.|
|Bearbeiten der Sperranzahl|Anzahl der Bearbeitungssperren. Eine Bearbeitungssperre gibt an, dass das Dokument für die Bearbeitung in einem Bestimmten Editor geöffnet ist. Wenn die Anzahl der Bearbeitungssperren auf Null übergeht, wird der Benutzer aufgefordert, das Dokument zu speichern, wenn es geändert wurde. Wenn Sie z. B. ein Dokument in einem Editor mit dem Befehl **Neues Fenster** öffnen, wird eine Bearbeitungssperre für dieses Dokument im RDT hinzugefügt. Damit eine Bearbeitungssperre festgelegt werden kann, muss das Dokument über eine Hierarchie- oder Element-ID verfügen.|
|Sperranzahl lesen|Anzahl der Lesesperren. Eine Lesesperre gibt an, dass das Dokument durch einen Mechanismus, z. B. einen Assistenten, gelesen wird. Eine Lesesperre hält ein Dokument im RDT am Leben und gibt an, dass das Dokument nicht bearbeitet werden kann. Sie können eine Lesesperre festlegen, auch wenn das Dokument keine Hierarchie- oder Element-ID hat. Mit dieser Funktion können Sie ein Dokument im Arbeitsspeicher öffnen und in die RDT eingeben, ohne dass das Dokument einer Hierarchie gehört. Diese Funktion wird selten verwendet.|
|Schlosshalter|Eine Instanz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> einer Schnittstelle. Der Sperrhalter wird durch Funktionen wie Assistenten implementiert, die Dokumente außerhalb eines Editors öffnen und bearbeiten. Ein Sperrhalter ermöglicht es dem Feature, dem Dokument eine Bearbeitungssperre hinzuzufügen, um zu verhindern, dass das Dokument geschlossen wird, während es noch bearbeitet wird. Normalerweise werden Bearbeitungssperren nur durch Dokumentfenster (d. h. Editoren) hinzugefügt.|

 Jedem Eintrag in der RDT ist eine eindeutige Hierarchie oder Element-ID zugeordnet, die im Allgemeinen einem Knoten im Projekt entspricht. Alle zur Bearbeitung verfügbaren Dokumente befinden sich in der Regel im Besitz einer Hierarchie. Einträge, die im RDT-Steuerelement vorgenommen werden, steuern, welches Projekt oder – genauer gesagt – welche Hierarchie derzeit das zu bearbeitende Dokumentdatenobjekt besitzt. Mithilfe der Informationen in der RDT kann die IDE verhindern, dass ein Dokument von mehreren Projektgleichzeitigen geöffnet wird.

 Die Hierarchie steuert auch die Persistenz von Daten und verwendet die Informationen in der RDT, um die Dialogfelder **Speichern** und **Speichern unter** zu aktualisieren. Wenn Benutzer ein Dokument ändern und dann im Menü **Datei** den Befehl **Beenden** auswählen, werden sie von der IDE im Dialogfeld **Änderungen** speichern aufgefordert, um ihnen alle Projekte und Projektelemente anzuzeigen, die derzeit geändert werden. Auf diese Weise können Benutzer auswählen, welche der Dokumente gespeichert werden sollen. Die Liste der zu speichernden Dokumente (d. h. die Dokumente mit Änderungen) wird aus dem RDT generiert. Alle Elemente, die beim Beenden der Anwendung im Dialogfeld **Änderungen** speichern angezeigt werden, sollten Datensätze im RDT enthalten. Die RDT-Koordinaten, welche Dokumente gespeichert werden und ob der Benutzer zu einem Speichervorgang aufgefordert wird, indem die im Eintrag Flags für jedes Dokument angegebenen Werte verwendet werden. Weitere Informationen zu den RDT-Flags finden Sie in der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Enumeration.

## <a name="edit-locks-and-read-locks"></a>Bearbeiten von Sperren und Lesesperren
 Bearbeiten von Sperren und Lesesperren befinden sich im RDT. Das Dokumentfenster erhöht und dekrementiert die Bearbeitungssperre. Wenn also ein Benutzer ein neues Dokumentfenster öffnet, erhöht sich die Anzahl der Bearbeitungssperren um eins. Wenn die Anzahl der Bearbeitungssperren Null erreicht, wird signalisiert, dass die Hierarchie beibehalten oder die Daten für das zugeordnete Dokument gespeichert werden. Die Hierarchie kann die Daten dann in irgendeiner Weise beibehalten, einschließlich der Beibehaltung als Datei oder als Element in einem Repository. Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> die Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> in der Schnittstelle verwenden, um <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Bearbeitungssperren und Lesesperren hinzuzufügen, sowie die Methode zum Entfernen dieser Sperren.

 Wenn das Dokumentfenster für einen Editor instanziiert wird, fügt der Fensterrahmen normalerweise automatisch eine Bearbeitungssperre für das Dokument im RDT hinzu. Wenn Sie jedoch eine benutzerdefinierte Ansicht eines Dokuments erstellen, das kein Standarddokumentfenster <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> verwendet (d. h. die Schnittstelle nicht implementiert), müssen Sie eine eigene Bearbeitungssperre festlegen. In einem Assistenten wird z. B. ein Dokument bearbeitet, ohne in einem Editor geöffnet zu werden. Damit Dokumentsperren von Assistenten und ähnlichen Entitäten geöffnet werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> können, müssen diese Entitäten die Schnittstelle implementieren. Um Ihren Dokumentsperrhalter zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> registrieren, rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Sie die Methode auf, und übergeben Sie die Implementierung. Auf diese Weise wird der Dokumentsperrhalter zum RDT hinzugefügt. Ein weiteres Szenario zum Implementieren eines Dokumentsperrhalters ist, wenn Sie ein Dokument über ein spezielles Werkzeugfenster öffnen. In diesem Fall können Sie das Dokument nicht im Werkzeugfenster schließen. Durch die Registrierung als Dokumentsperrhalter im RDT kann die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> jedoch Ihre Implementierung der Methode aufrufen, um einen Abschluss des Dokuments einzufordern.

## <a name="other-uses-of-the-running-document-table"></a>Andere Verwendungen der Tabelle "Laufende sernende Dokument"
 Andere Entitäten in der IDE verwenden die RDT, um Informationen über Dokumente zu erhalten. Beispielsweise verwendet der Quellcodeverwaltungs-Manager die RDT, um das System anzuweisen, ein Dokument im Editor neu zu laden, nachdem es die neueste Version der Datei erhalten hat. Zu diesem Tun sucht der Quellcodeverwaltungs-Manager die Dateien im RDT, um zu sehen, ob eine von ihnen geöffnet ist. Wenn dies der Zeitpunkt ist, überprüft der Quellcodeverwaltungs-Manager zuerst, ob die Hierarchie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode implementiert. Wenn das Projekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode nicht implementiert, sucht der Quellcodeverwaltungs-Manager direkt nach einer Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Methode für das Dokumentdatenobjekt.

 Die IDE verwendet die RDT auch, um ein geöffnetes Dokument wieder aufzutauchen (nach vorne zu bringen), wenn ein Benutzer dieses Dokument anfordert. Weitere Informationen finden Sie unter [Anzeigen von Dateien mithilfe des Befehls Datei öffnen](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Um zu ermitteln, ob eine Datei in der RDT geöffnet ist, gehen Sie wie folgt vor.

- Abfrage für den Dokumentmoniker (d. h. den vollständigen Dokumentpfad), um herauszufinden, ob das Element geöffnet ist.

- Verwenden Sie die Hierarchie oder Element-ID, um das Projektsystem nach dem vollständigen Dokumentpfad zu fragen, und suchen Sie dann das Element in der RDT nach oben.

## <a name="see-also"></a>Weitere Informationen
- [RDT_ReadLock-Verwendung](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistenz und die aktive Dokumenttabelle](../../extensibility/internals/persistence-and-the-running-document-table.md)
