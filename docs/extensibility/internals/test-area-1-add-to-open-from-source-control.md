---
title: 'Testbereich 1: Hinzufügen von To-Open von der Quellcodeverwaltung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704677"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Testbereich 1: Hinzufügen zu/Öffnen von der Quellcodeverwaltung
Dieser Quellcodeverwaltungs-Plug-In-Testbereich umfasst das Platzieren von Lösungen oder Projekten unter Quellcodeverwaltung und deren Abrufen aus der Quellcodeverwaltung.

## <a name="command-menu-access"></a>Befehlsmenüzugriff
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Testfällen werden die folgenden integrierten Menüpfade für entwicklungsumgebungverwendet:

- Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]öffnen sie aus der Quellcodeverwaltung: **Datei**, **Öffnen**,**Projektmappe** **Project**/; in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Position suchen.

- Für andere Quellcodeverwaltungs-Plug-Ins, öffnen Sie von der Quellcodeverwaltung: **Datei**, **Quellcodeverwaltung**, **Von Der Quellcodeverwaltung geöffnet**.

- Zur Quellcodeverwaltung hinzufügen: **Datei**, **Quellcodeverwaltung**, **Lösung zur Quellcodeverwaltungsdatei hinzufügen**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.

- Shortcut-Menü (Projekt/Projektmappe), **Lösung zur Quellcodeverwaltung hinzufügen**.

- Aus der Quellcodeverwaltung hinzufügen: **Datei**, **Quellcodeverwaltung**, **Projekt aus der Quellcodeverwaltung hinzufügen**.

- Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]ist add from source control auch unter **Datei**, **Hinzufügen**, **Vorhandenes Projekt**verfügbar . in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Position suchen.

  > [!NOTE]
  > In diesem Test kann ein Pfad einer lokalen Datei oder eines lokalen IIS (Webserver) verwendet werden.

## <a name="expected-behavior"></a>Erwartetes Verhalten

- Für jeden unterstützten Projekttyp sollte ein Benutzer in der Lage sein, die Quellcodeverwaltung "Hinzufügen" und "Öffnen von" zu erstellen.

- Wenn ein Projekt zur Quellcodeverwaltung \<hinzugefügt wird, wird eine entsprechende *ProjectName*>.vspscc-Datei (Projekt-Hinweisdatei) erstellt. Sie enthält Ausschlussdateilisten und Verbindungsinformationen. Löschen Sie diese Datei nicht, da sie projektspezifische Informationen enthält.

- Wenn eine Lösung zur Quellcodeverwaltung \<hinzugefügt wird, wird eine entsprechende *SolutionName-datei*>.vssscc (Triple S) erstellt. Die Textdatei enthält Verbindungsinformationen und eine Ausschlussdateiliste, ähnlich der Projekthinweisdatei. Diese Datei ist temporär und nur in der Quellcodeverwaltungsdatenbank vorhanden.

- Wenn eine Lösung aus der \<Quellcodeverwaltung geöffnet wird, wird eine *SolutionName*>.vsscc-Datei (doppelteS) Datei, die nur in der Quellcodeverwaltungsdatenbank vorhanden ist, lokal in einer temporären Datei erstellt. Diese Datei enthält den Pfad aus dem Lösungsverbindungsordner zur Projektmappendatei. Diese Datei ist temporär und die lokale Kopie wird gelöscht, wenn der Vorgang "Öffnen aus der Quellcodeverwaltung" abgeschlossen ist.

- Nachdem ein Projekt der Quellcodeverwaltung hinzugefügt wurde, können Sie alle Quellcodeverwaltungsaktionen darauf ausführen (Auschecken, Abrufen usw.).

## <a name="test-cases"></a>Testfälle
 Im Folgenden finden Sie spezifische Testfälle für den Testbereich "Hinzufügen zu/Öffnen von Der Quellcodeverwaltung".

### <a name="case-1a-add-solution-to-source-control"></a>Fall 1a: Hinzufügen einer Lösung zur Quellcodeverwaltung
 Dieser Testfall konzentriert sich auf das Hinzufügen von Lösungen zur Quellcodeverwaltung.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Hinzufügen einer Projektmappe, die ein Clientprojekt zur Quellcodeverwaltung enthält|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Lösung zur Quellcodeverwaltung hinzufügen**).|Projektmappe/Projekt wurde der Quellcodeverwaltung hinzugefügt.|
|Hinzufügen einer Projektmappe, die ein Dateisystem oder ein lokales IIS-Webprojekt zur Quellcodeverwaltung enthält|1. Erstellen Sie ein Dateisystem oder ein lokales IIS-Webprojekt (verwenden Sie die Schaltfläche Durchsuchen, um auf den Speicherort des Projekts zu zeigen; der Pfad bestimmt, welcher Typ des Webprojekts erstellt wird).<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Lösung zur Quellcodeverwaltung hinzufügen**).|Projektmappe/Projekt wurde der Quellcodeverwaltung hinzugefügt.|
|Hinzufügen einer Projektmappe, die ein Remotesite-Webprojekt zur Quellcodeverwaltung enthält|1. Erstellen Sie ein Remotesite-Webprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Lösung zur Quellcodeverwaltung hinzufügen**).<br />3. Klicken Sie im Warndialogfeld FrontPage Access auf **OK.**|Die Lösung wurde der Quellcodeverwaltung hinzugefügt.<br /><br /> Remote Site-Projekt ist NICHT unter Quellcodeverwaltung. (Remotestandortprojekte müssen von ihrem eigenen IIS-Server aus gesteuert werden.)|
|Fügen Sie der Quellcodeverwaltung mithilfe ausgewählte **Projekte zur Quellcodeverwaltung**hinzufügen hinzu.|1. Erstellen Sie eine einzelne Projektmappe.<br />2. Fügen Sie der Quellcodeverwaltung als Auswahl nur eine Lösung hinzu (**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung**hinzufügen ). Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Fügen Sie Projekt zur Quellcodeverwaltung als Auswahl hinzu (**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**).<br />4. Klicken Sie auf **Ja,** um das Projekt am selben Speicherort hinzuzufügen.<br />5. Klicken Sie im Dialogfeld **Auschecken für Bearbeiten** auf **Auschecken.**|`Result from Step 2:`<br /><br /> Das Projekt und alle Dateien innerhalb des Projekts verfügen über eine ausgecheckte Quellcodeverwaltungsanzeige, und ein ToolTip zeigt "Nicht unter Quellcodeverwaltung" an.<br /><br /> `Result from Step 5:`<br /><br /> Projekt- und Projektmappendatei befinden sich im gleichen Ordner in der Quellcodeverwaltung.|
|Abbrechen des Hinzufügens einer Lösung zur Quellcodeverwaltung|1. Erstellen Sie eine einzelne Projektmappe.<br />2. Versuchen Sie, Projekt und Projektmappe zur Quellcodeverwaltung hinzuzufügen. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Abbrechen, nachdem Sie sich im Quellcodeverwaltungssystem befinden.|`Result from Step 2:`<br /><br /> Das Dialogfeld Projektstandortsteuerung festlegen wird nur einmal angezeigt.<br /><br /> `Result from Step 3:`<br /><br /> Projekt-Add abgebrochen, Projekt/Lösung ist NICHT unter Quellcodeverwaltung und alle Menüs zur Quellcodeverwaltung hinzufügen sind weiterhin verfügbar.|

### <a name="case-1b-open-solution-from-source-control"></a>Fall 1b. Open Solution von Source Control
 Dieser Testfall konzentriert sich auf das Öffnen von Lösungen aus der Quellcodeverwaltung.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Öffnen einer Projektmappe, die ein Clientprojekt aus der Quellcodeverwaltung enthält|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schließen Sie die Lösung.<br />4. Öffnen Sie die Lösung von der Quellcodeverwaltung zu einem neuen Speicherort.|Projektmappe/Projekt, das von der Quellcodeverwaltung aus geöffnet wurde.|
|Öffnen einer Projektmappe, die ein lokales oder IIS-Webprojekt aus der Quellcodeverwaltung enthält|1. Erstellen Sie ein lokales oder IIS-Webprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schließen Sie die Lösung.<br />4. Öffnen Sie die Lösung von der Quellcodeverwaltung zu einem neuen Speicherort.|Projektmappe/Projekt, das von der Quellcodeverwaltung aus geöffnet wurde.|
|Öffnen einer Projektmappe, die ein Remote site-Webprojekt aus der Quellcodeverwaltung enthält|1. Erstellen Sie ein Remotesite-Webprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Schließen Sie die Lösung.<br />4. Öffnen Sie die Lösung von der Quellcodeverwaltung zu einem neuen Speicherort.|`Result from Step 2:`<br /><br /> Remote Site Web ist NICHT unter Quellcodeverwaltung.<br /><br /> `Result from Step 4:`<br /><br /> Lösung, die von der Quellcodeverwaltung aus geöffnet wurde.<br /><br /> Remote Site-Projekt wird geladen, ist aber NICHT unter Quellcodeverwaltung.|

### <a name="case-1c-add-solution-from-source-control"></a>Fall 1c: Hinzufügen einer Lösung aus der Quellcodeverwaltung
 Dieser Testfall konzentriert sich auf das Hinzufügen von Lösungen aus der Quellcodeverwaltung.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Hinzufügen zu Empty-Projektmappe – eine einzelne Projektmappe|1. Erstellen Sie eine einzelne Projektmappe.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schließen Sie die Lösung.<br />4. Erstellen Sie eine zweite leere Lösung.<br />5. Fügen Sie die zuvor gesteuerte Lösung aus der Quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Projekt aus der Quellcodeverwaltung hinzufügen**).|Das hinzugefügte Projekt wird im **Projektmappen-Explorer** angezeigt und eingecheckt.|
|Hinzufügen zur Projektmappe mit einem einzelnen Projekt — einzelprojekt|1. Erstellen Sie eine Projektmappe mit einem einzelnen Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schließen Sie die Lösung.<br />4. Erstellen Sie eine zweite leere Lösung.<br />5. Fügen Sie die zuvor gesteuerte Lösung aus der Quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Projekt aus der Quellcodeverwaltung hinzufügen**).|Das hinzugefügte Projekt wird im **Projektmappen-Explorer** angezeigt und eingecheckt.|
|Zur Lösung hinzufügen – Lösung, die der Quellcodeverwaltung nach Auswahl hinzugefügt wird|1. Erstellen Sie eine Projektmappe mit einem Projekt.<br />2. Fügen Sie der Quellcodeverwaltung als Auswahl nur eine Lösung hinzu. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Schließen Sie die Lösung.<br />4. Erstellen Sie eine neue Lösung.<br />5. Fügen Sie die zuvor gesteuerte Lösung aus der Quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Projekt aus der Quellcodeverwaltung hinzufügen**).|`Result from Step 2:`<br /><br /> Project befindet sich nicht unter Quellcodeverwaltung.<br /><br /> `Result from Step 5:`<br /><br /> Wenn die erste Lösung Lösungselemente hatte, können sie nicht aus der Quellcodeverwaltung hinzugefügt werden, sodass sie nicht angezeigt werden.<br /><br /> Project von der ersten Projektmappe wird als nicht verfügbar angezeigt.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
