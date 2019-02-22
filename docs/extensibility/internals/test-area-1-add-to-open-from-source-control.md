---
title: 'Testbereich 1: Hinzufügen / öffnen aus der Quellcodeverwaltung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 686c7fbfae76d9f4006664aff9f79848eba563f8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613316"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Testbereich 1: Fügen Sie in / öffnen aus der Quellcodeverwaltung hinzu.
Diese quellcodeverwaltung-Plug-in testen Bereich erläutert das Platzieren von Projektmappen oder Projekte unter quellcodeverwaltung und Abrufen von Verbindungszeichenfolgen aus der quellcodeverwaltung.

## <a name="command-menu-access"></a>Menüzugriff Befehl
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Development-Umgebung im Menüpfade werden verwendet, in den Testfällen:

- Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]aus der quellcodeverwaltung öffnen: **Datei**, **öffnen**, **Projekt**/**Lösung**; Suchen in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.

- Öffnen Sie für andere Quellcodeverwaltungs-Plug-ins aus der quellcodeverwaltung: **Datei**, **Quellcodeverwaltung**, **aus Quellcodeverwaltung öffnen**.

- Zur quellcodeverwaltung hinzufügen: **Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltungsdatei Lösung hinzugefügt**, **Quellcodeverwaltung**, **ausgewählte Projekte zur QuellcodeverwaltungHinzufügen**.

- Im Kontextmenü (Projekt/Projektmappe), **Projektmappe zur Quellcodeverwaltung hinzufügen**.

- Fügen Sie aus der quellcodeverwaltung hinzu: **Datei**, **Quellcodeverwaltung**, **Projekt aus der Quellcodeverwaltung hinzufügen**.

- Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Hinzufügen von Quelle Steuerelement steht auch auf **Datei**, **hinzufügen**, **vorhandenes Projekt**; Suchen in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.

  > [!NOTE]
  >  Ein Pfad von einer lokalen Datei oder eine lokale IIS (Webserver) kann in diesem Test verwendet werden.

## <a name="expected-behavior"></a>Es wird erwartet

-   Für jede unterstützte Projekttyp muss ein Benutzer können Sie "Hinzufügen" und "Öffnen in" Datenquellen-Steuerelement.

-   Wenn ein Projekt zur Quellcodeverwaltung, ein entsprechendes hinzugefügt wird \< *ProjectName*> .vspscc-Datei (Projektdatei Hinweis) erstellt wird. Es enthält Informationen von Ausschluss-Datei Liste und die Verbindungszeichenfolge. Diese Datei kann nicht gelöscht werden, da sie Informationen, die spezifisch für das Projekt enthält.

-   Wenn eine Projektmappe zur quellcodeverwaltung, ein entsprechendes hinzugefügt wird \< *SolutionName*> .vssscc (Tripel S)-Datei erstellt wird. Die Textdatei enthält die Verbindungsinformationen und eine Datei Ausschlussliste, ähnlich wie die Hinweis-Projektdatei. Diese Datei besteht nur vorübergehend und nur im Quellcode-Verwaltungsdatenbank vorhanden ist.

-   Wenn eine Projektmappe, aus der quellcodeverwaltung geöffnet ist eine \< *SolutionName*> .vsscc (double-S)-Datei, die nur in der Quellcode-Verwaltungsdatenbank vorhanden ist wird lokal in eine temporäre Datei erstellt. Diese Datei enthält den Pfad aus dem Projektmappenordner für die Verbindung zur Projektmappendatei. Diese Datei ist vorübergehend, und die lokale Kopie wird gelöscht, wenn der Vorgang "Aus Quellcodeverwaltung öffnen" abgeschlossen wurde.

-   Nachdem ein Projekt der quellcodeverwaltung hinzugefügt wurde, können Sie alle Datenquellen-Steuerelement-Aktionen auf (sehen Sie sich, Get usw.) ausführen.

## <a name="test-cases"></a>Testfälle
 Im folgenden sind bestimmte Testfälle für das Hinzufügen zu / von Testbereich Quellcodeverwaltung öffnen.

### <a name="case-1a-add-solution-to-source-control"></a>Groß-/Kleinschreibung 1a: Projektmappe zur Quellcodeverwaltung hinzufügen
 Dieser Testfall konzentriert sich auf Lösungen zur quellcodeverwaltung hinzufügen.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Fügen Sie Lösung mit einer Client-Projekt zur quellcodeverwaltung hinzu|1.  Erstellen Sie ein Clientprojekt.<br />2.  Die Projektmappe zur quellcodeverwaltung hinzufügen (**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Quellcodeverwaltung hinzufügen**).|Datenquellen-Steuerelement wurde der Projektmappe oder eines Projekts hinzugefügt.|
|Fügen Sie Lösung mit einem Dateisystem oder dem lokalen IIS-Web-Projekt zur quellcodeverwaltung hinzu|1.  Erstellen Sie eine Dateisystem oder dem lokalen IIS-Webprojekt (verwenden Sie die Schaltfläche "Durchsuchen", zeigen Sie zum Speicherort des Projekts des Pfads bestimmt, welche Art von Web-Projekt erstellt wird).<br />2.  Die Projektmappe zur quellcodeverwaltung hinzufügen (**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Quellcodeverwaltung hinzufügen**).|Datenquellen-Steuerelement wurde der Projektmappe oder eines Projekts hinzugefügt.|
|Fügen Sie Lösung mit einem Remotewebzugriff-Website-Projekt zur quellcodeverwaltung hinzu|1.  Erstellen Sie ein Projekt für die Remotewebzugriff-Website.<br />2.  Die Projektmappe zur quellcodeverwaltung hinzufügen (**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Quellcodeverwaltung hinzufügen**).<br />3.  Klicken Sie auf **OK** im Dialogfeld "Warnung" FrontPage-Zugriff.|Datenquellen-Steuerelement wurde der Projektmappe hinzugefügt.<br /><br /> Remote-Websiteprojekt ist nicht unter quellcodeverwaltung. (Remote-Standortsystemserver Projekte müssen aus ihrem eigenen IIS-Server kontrolliert werden.)|
|Hinzufügen eine einzelnen Projektmappe mit Source Control **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.|1.  Erstellen einer Lösung für die einzelnen Projekts.<br />2.  Nur die Projektmappe zur quellcodeverwaltung als Auswahl hinzufügen (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**). Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />3.  Hinzufügen von Projekt zur quellcodeverwaltung wie Auswahl (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**).<br />4.  Klicken Sie auf **Ja** am gleichen Speicherort des Projekts hinzu.<br />5.  Klicken Sie auf **Auschecken** in **Auschecken zum Bearbeiten** Dialogfeld.|`Result from Step 2:`<br /><br /> Das Projekt und alle Dateien innerhalb des Projekts haben Sie Source Control Indikator einen aktivierten, und eine QuickInfo angezeigt wird, "nicht unter quellcodeverwaltung".<br /><br /> `Result from Step 5:`<br /><br /> Projekt-und Projektmappendatei befinden sich in demselben Ordner in der quellcodeverwaltung.|
|Brechen Sie eine Projektmappe zur quellcodeverwaltung hinzufügen ab|1.  Erstellen einer Lösung für die einzelnen Projekts.<br />2.  Es wurde versucht, das Projekt und Projektmappe zur quellcodeverwaltung hinzufügen. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />3.  Abbrechen Sie, wenn Sie im Quellcode-Verwaltungssystems sind.|`Result from Step 2:`<br /><br /> Das Dialogfeld Satz Projekt Speicherort Source Control wird nur einmal angezeigt.<br /><br /> `Result from Step 3:`<br /><br /> Projekt hinzufügen wurde abgebrochen, Projekt/Projektmappe befindet sich nicht unter quellcodeverwaltung und alle Datenquellen-Steuerelement Menüs weiterhin verfügbar hinzufügen.|

### <a name="case-1b-open-solution-from-source-control"></a>Fall 1 b. Die Projektmappe aus der Quellcodeverwaltung öffnen
 Dieser Testfall konzentriert sich auf Lösungen aus der quellcodeverwaltung öffnen.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Öffnen Sie eine Projektmappe mit einem Clientprojekt aus der quellcodeverwaltung|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort ein.|Projektmappe oder eines Projekts aus der quellcodeverwaltung geöffnet.|
|Öffnen Sie eine Projektmappe mit einem lokalen oder den IIS-Web-Projekt aus der quellcodeverwaltung|1.  Erstellen Sie eine lokale oder eine IIS-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort ein.|Projektmappe oder eines Projekts aus der quellcodeverwaltung geöffnet.|
|Öffnen Sie eine Projektmappe mit einem Remote-Website-Webprojekt aus der quellcodeverwaltung|1.  Erstellen Sie ein Projekt für die Remotewebzugriff-Website.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort ein.|`Result from Step 2:`<br /><br /> Remotewebzugriff-Website ist nicht unter quellcodeverwaltung.<br /><br /> `Result from Step 4:`<br /><br /> Lösung, die aus der quellcodeverwaltung geöffnet werden.<br /><br /> Remote-Websiteprojekt wird geladen, aber es ist nicht unter quellcodeverwaltung.|

### <a name="case-1c-add-solution-from-source-control"></a>Fall 1c: Fügen Sie die Lösung aus der Quellcodeverwaltung hinzu
 Dieser Testfall konzentriert sich auf Lösungen aus der quellcodeverwaltung hinzufügen.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Leere Projektmappe hinzufügen, eine Lösung für die einzelnen Projekt|1.  Erstellen einer Lösung für die einzelnen Projekts.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine zweite leere Projektmappe.<br />5.  Die Lösung für die zuvor kontrollierte aus der quellcodeverwaltung hinzufügen (**Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**).|Das hinzugefügte Projekt wird im **Projektmappen-Explorer** und eingecheckt ist.|
|Lösung mit einzelnen Projekt hinzuzufügen, einzelnen Projekt|1.  Erstellen Sie eine Projektmappe mit einem einzelnen Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine zweite leere Projektmappe.<br />5.  Die Lösung für die zuvor kontrollierte aus der quellcodeverwaltung hinzufügen (**Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**).|Das hinzugefügte Projekt wird im **Projektmappen-Explorer** und eingecheckt ist.|
|Zu Projektmappe hinzufügen – Projektmappe zur quellcodeverwaltung hinzugefügt werden, durch Auswahl|1.  Erstellen Sie eine Projektmappe mit einem Projekt ein.<br />2.  Fügen Sie nur die Projektmappe zur quellcodeverwaltung hinzu, als Auswahl. Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine neue Projektmappe.<br />5.  Die Lösung für die zuvor kontrollierte aus der quellcodeverwaltung hinzufügen (**Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**).|`Result from Step 2:`<br /><br /> Projekt kann nicht unter quellcodeverwaltung.<br /><br /> `Result from Step 5:`<br /><br /> Wenn die erste Lösung Projektmappenelemente haben, können nicht sie aus der quellcodeverwaltung hinzugefügt werden, damit sie nicht angezeigt werden.<br /><br /> Projekt aus der ersten Lösung wird als nicht verfügbar angezeigt.|

## <a name="see-also"></a>Siehe auch
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)