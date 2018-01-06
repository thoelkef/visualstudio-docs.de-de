---
title: "Testbereich 1: Hinzufügen zu öffnen, aus der Quellcodeverwaltung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1891e0242463f3673d22d22e0f9a2d000b01ae60
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Testbereich 1: Fügen Sie hinzu, / Open-aus der Quellcodeverwaltung
Dieses Plug-in-Quelle-Steuerelement testen Bereich deckt Projektmappen oder Projekten unter quellcodeverwaltung platzieren und aus der quellcodeverwaltung abrufen.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfade in den Testfällen verwendet werden:  
  
-   Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]aus der quellcodeverwaltung öffnen: **Datei**, **öffnen**, **Projekt**/**Lösung**; Suchen in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.  
  
-   Öffnen Sie für andere Datenquellen-Steuerelement-Plug-ins, aus der quellcodeverwaltung: **Datei**, **Quellcodeverwaltung**, **aus Quellcodeverwaltung öffnen**.  
  
-   Zur quellcodeverwaltung hinzufügen: **Datei**, **Quellcodeverwaltung**, **Projektmappe hinzufügen, zu der Quellcodeverwaltungsdatei**, **Quellcodeverwaltung**, **hinzufügen Ausgewählte Projekte zur Quellcodeverwaltung**.  
  
-   Kontextmenü (Projektmappe), **Projektmappe zur Quellcodeverwaltung hinzufügen**.  
  
-   Hinzufügen von Datenquellen-Steuerelements: **Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**.  
  
-   Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Hinzufügen von Quelle Steuerelement steht auch auf **Datei**, **hinzufügen**, **vorhandenes Projekt**; Suchen in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.  
  
    > [!NOTE]
    >  Ein Pfad für eine lokale Datei oder eine lokale IIS (Webserver) kann in diesem Test verwendet werden.  
  
## <a name="expected-behavior"></a>Erwartetes Verhalten  
  
-   Für jeden unterstützten Projekttyps muss ein Benutzer kann "Hinzufügen" und "Geöffnet von" Quellcodeverwaltung.  
  
-   Wenn ein Projekt zur Quellcodeverwaltung, ein entsprechendes hinzugefügt wird \< *Projektname*> .vspscc-Datei (Projekt Hint-Datei) erstellt wird. Es enthält Ausschluss Datei Liste und Verbindung. Diese Datei kann nicht gelöscht werden, da sie speziell für das Projekt enthält.  
  
-   Wenn eine Projektmappe zur quellcodeverwaltung, ein entsprechendes hinzugefügt wird \< *SolutionName*> .vssscc (Triple S)-Datei wird erstellt. Die Textdatei enthält Verbindungsinformationen und eine Datei Ausschlussliste, ähnlich wie das Projekt Hint-Datei. Diese Datei ist temporär und nur in der Quellcode-Verwaltungsdatenbank vorhanden ist.  
  
-   Wenn eine Projektmappe, aus der quellcodeverwaltung geöffnet ist eine \< *SolutionName*> .vsscc (double-S)-Datei, die nur in der Quellcode-Verwaltungsdatenbank, vorhanden ist, wird lokal in einer temporären Datei erstellt. Diese Datei enthält den Pfad im Projektmappenordner für die Verbindung zur Projektmappendatei. Diese Datei ist temporär, und die lokale Kopie wird gelöscht, wenn der Vorgang "Aus Quellcodeverwaltung öffnen" abgeschlossen wurde.  
  
-   Nachdem ein Projekt der quellcodeverwaltung hinzugefügt wurde, können Sie alle Datenquellen-Steuerelement-Aktionen (Auschecken, Get, usw.) ausführen.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden sind bestimmte Testfälle für das Hinzufügen zu / von Testbereich Quellcodeverwaltung öffnen.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Case-1a: Hinzufügen von Projektmappen zur Quellcodeverwaltung  
 Dieser Testfall konzentriert sich auf das Hinzufügen von Projektmappen zur quellcodeverwaltung.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Fügen Sie Lösung mit einem Clientprojekt zur quellcodeverwaltung hinzu|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie die Projektmappe zur quellcodeverwaltung (**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Quellcodeverwaltung hinzufügen**).|Projektmappe/Projekt wurde zur quellcodeverwaltung hinzugefügt.|  
|Fügen Sie Lösung mit einem Dateisystem oder einem lokalen IIS-Web-Projekt zur quellcodeverwaltung hinzu|1.  Ein Dateisystem oder dem lokalen IIS-Webprojekt zu erstellen (Schaltfläche "Durchsuchen" zum Verweisen auf den Projektspeicherort; Verwenden des Pfads bestimmt, welche Art von Webprojekt erstellt wird).<br />2.  Fügen Sie die Projektmappe zur quellcodeverwaltung (**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Quellcodeverwaltung hinzufügen**).|Projektmappe/Projekt wurde zur quellcodeverwaltung hinzugefügt.|  
|Fügen Sie Lösung mit einem Remotewebzugriff-Website-Projekt zur quellcodeverwaltung hinzu|1.  Erstellen Sie ein Projekt für die Remotewebzugriff-Website.<br />2.  Fügen Sie die Projektmappe zur quellcodeverwaltung (**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Quellcodeverwaltung hinzufügen**).<br />3.  Klicken Sie auf **OK** im Dialogfeld "Warnung" FrontPage-Zugriff.|Lösung wurde zur quellcodeverwaltung hinzugefügt.<br /><br /> Remote-Websiteprojekt liegt nicht unter quellcodeverwaltung. (Remotestandort Projekte müssen auf ihre eigenen IIS-Server kontrolliert werden.)|  
|Fügen Sie eine einzelne Projektmappe mit Source Control **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.|1.  Erstellen Sie eine einzelne Projektmappe.<br />2.  Hinzufügen von nur Projektmappe zur quellcodeverwaltung als Auswahl (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />3.  Add-Projekt zur quellcodeverwaltung als Auswahl (**Datei**, **Quellcodeverwaltung**, **ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**).<br />4.  Klicken Sie auf **Ja** am gleichen Speicherort des Projekts hinzu.<br />5.  Klicken Sie auf **Auschecken** in **Auschecken zum Bearbeiten** (Dialogfeld).|`Result from Step 2:`<br /><br /> Das Projekt und alle Dateien innerhalb des Projekts out Source Control Indikator ein aktiviert haben, und "nicht in der quellcodeverwaltung" in einer QuickInfo angezeigt.<br /><br /> `Result from Step 5:`<br /><br /> Projekt- und Projektmappendateien-Datei werden im selben Ordner im Datenquellen-Steuerelements.|  
|"Abbrechen", die beim Hinzufügen einer Projektmappe zur quellcodeverwaltung|1.  Erstellen Sie eine einzelne Projektmappe.<br />2.  Beim Hinzufügen von Projekt- und Projektmappendateien zur quellcodeverwaltung. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />3.  Brechen Sie ab, nachdem Sie sich im Quellcodeverwaltungssystem befinden.|`Result from Step 2:`<br /><br /> Der Satz Projekt Source Control Dialogfeld "Standort" wird nur einmal angezeigt.<br /><br /> `Result from Step 3:`<br /><br /> Projekt hinzufügen wurde abgebrochen, Projekt/Projektmappe ist nicht in der quellcodeverwaltung und alle hinzufügen Source Control Menüs weiterhin verfügbar.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>Groß-/Kleinschreibung 1 b. Geöffnete Projektmappe aus der Quellcodeverwaltung  
 Dieser Testfall konzentriert sich auf Lösungen aus der quellcodeverwaltung öffnen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Öffnen Sie eine Projektmappe enthält ein Clientprojekt aus der quellcodeverwaltung|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort.|Projektmappe/Projekt aus der quellcodeverwaltung geöffnet.|  
|Öffnen Sie eine Projektmappe mit einer lokalen oder IIS-Webprojekt aus der quellcodeverwaltung|1.  Erstellen Sie eine lokale oder eine IIS-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort.|Projektmappe/Projekt aus der quellcodeverwaltung geöffnet.|  
|Öffnen Sie eine Projektmappe mit einem Remotewebzugriff-Website-Projekt aus der quellcodeverwaltung|1.  Erstellen Sie ein Projekt für die Remotewebzugriff-Website.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus der quellcodeverwaltung an einem neuen Speicherort.|`Result from Step 2:`<br /><br /> Remotewebzugriff-Website ist nicht in der quellcodeverwaltung.<br /><br /> `Result from Step 4:`<br /><br /> Die Lösung aus der quellcodeverwaltung geöffnet.<br /><br /> Remote-Websiteprojekt wird geladen, aber es ist nicht in der quellcodeverwaltung.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Fall 1c: Hinzufügen von Projektmappen aus der Quellcodeverwaltung  
 Dieser Testfall konzentriert sich auf das Hinzufügen von Projektmappen aus der quellcodeverwaltung.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Leere Projektmappe hinzugefügt – eine einzelne Projektmappe|1.  Erstellen Sie eine einzelne Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine zweite leere Projektmappe.<br />5.  Fügen Sie die zuvor kontrollierten Lösung aus der quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**).|Das hinzugefügte Projekt wird im **Projektmappen-Explorer** und aktiviert ist.|  
|Lösung mit einzelnen Projekt hinzufügen – einzelnes Projekt|1.  Erstellen Sie eine Projektmappe mit einem einzelnen Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine zweite leere Projektmappe.<br />5.  Fügen Sie die zuvor kontrollierten Lösung aus der quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**).|Das hinzugefügte Projekt wird im **Projektmappen-Explorer** und aktiviert ist.|  
|Zu Projektmappe hinzufügen – Projektmappe zur quellcodeverwaltung durch Auswahl hinzugefügt|1.  Erstellen Sie eine Projektmappe mit einem Projekt ein.<br />2.  Fügen Sie nur Projektmappen zur quellcodeverwaltung hinzu, als Auswahl. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächsten Schritt fort.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine neue Projektmappe.<br />5.  Fügen Sie die zuvor kontrollierten Lösung aus der quellcodeverwaltung hinzu (**Datei**, **Quellcodeverwaltung**, **Projekt hinzufügen, aus der Quellcodeverwaltung**).|`Result from Step 2:`<br /><br /> Projekt kann nicht in der quellcodeverwaltung.<br /><br /> `Result from Step 5:`<br /><br /> Wenn für die erste Lösung Projektmappenelemente wurde, können sie aus der quellcodeverwaltung hinzugefügt werden, damit sie nicht angezeigt werden.<br /><br /> Projekt aus der ersten Lösung wird als nicht verfügbar angezeigt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)