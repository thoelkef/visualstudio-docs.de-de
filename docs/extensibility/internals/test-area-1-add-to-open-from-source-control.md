---
title: "Testbereich 1: F&#252;gen Sie zu &#246;ffnen hinzu, From Source Control | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellen-Steuerelement [Visual Studio SDK], hinzufügen und Öffnen von Projektmappen"
  - "Source Control-Plug-ins hinzufügen und Öffnen von Projektmappen"
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Testbereich 1: F&#252;gen Sie und &#214;ffnen von Datenquellen-Steuerelement hinzu
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieses plug\-in Quellkontrollserver testen Bereich erläutert das Platzieren von Projektmappen oder Projekten unter quellcodeverwaltung und Abrufen von Verbindungszeichenfolgen aus Datenquellen\-Steuerelement.  
  
## Befehl Menüzugriff  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development\-Umgebung im Menüpfade in den Testfällen verwendet werden:  
  
-   Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Öffnen von Datenquellen\-Steuerelement: **Datei**, **Öffnen**, **Projekt**\/**Lösung**; Suchen in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.  
  
-   Öffnen Sie für andere Source Control\-Plug\-ins über Datenquellen\-Steuerelement: **Datei**, **Source Control**, **from Source Control öffnen**.  
  
-   Zur Versionskontrolle hinzufügen: **Datei**, **Source Control**, **Projektmappe hinzufügen, um Quellcodeverwaltungsdatei**, **Source Control**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.  
  
-   Kontextmenü \(Projektmappe\), **Projektmappe zur Versionskontrolle hinzufügen**.  
  
-   Hinzufügen von Datenquellen\-Steuerelement: **Datei**, **Quellcodeverwaltung**, **Add Project from Source Control**.  
  
-   Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Hinzufügen von Quelle Steuerelement steht auch in **Datei**, **Hinzufügen**, **Vorhandenes Projekt**; Suchen in der [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.  
  
    > [!NOTE]
    >  Ein Pfad für eine lokale Datei oder eine lokale IIS \(Webserver\) kann in diesem Test verwendet werden.  
  
## Es wird erwartet  
  
-   Für jeden unterstützten Projekttyp sollte ein Benutzer in der Lage "Hinzufügen" und "Öffnen" Datenquellen\-Steuerelement.  
  
-   Wenn ein Projekt für die Datenquellen\-Steuerelement, ein entsprechendes hinzugefügt wird \<*Projektname*\> .vspscc\-Datei \(Projekt\-Hint\-Datei\) erstellt. Es enthält Ausschluss Datei Liste und Verbindung. Diese Datei kann nicht gelöscht werden, da sie speziell für das Projekt enthält.  
  
-   Wenn eine Projektmappe zur Versionskontrolle, ein entsprechendes hinzugefügt wird \<*SolutionName*\> .vssscc \(Dreifach\-S\)\-Datei wird erstellt. Die Textdatei enthält Verbindungsinformationen und eine Datei Ausschlussliste, ähnlich wie die Projektdatei Hinweis. Diese Datei ist temporär und nur in der Quellcode\-Verwaltungsdatenbank vorhanden.  
  
-   Beim Öffnen einer Projektmappe aus Datenquellen\-Steuerelement, ein \<*SolutionName*\> .vsscc \(double\-S\)\-Datei, die nur in der Quellcode\-Verwaltungsdatenbank vorhanden ist lokal in einer temporären Datei erstellt. Diese Datei enthält den Pfad zur Projektmappendatei im Projektmappenordner für die Verbindung. Diese Datei ist vorübergehend, und die lokale Kopie wird gelöscht, wenn der Vorgang "Aus Quellcodeverwaltung öffnen" abgeschlossen wurde.  
  
-   Nachdem ein Projekt für das Datenquellen\-Steuerelement hinzugefügt wird, können Sie alle Datenquellen\-Steuerelement\-Aktionen auf \(Auschecken, Get usw.\) ausführen.  
  
## Testfälle  
 Im folgenden sind bestimmte Testfälle für das Hinzufügen und Öffnen von Datenquellen\-Steuerelement Testbereich.  
  
### Case\-1a: Projektmappe zur Versionskontrolle hinzufügen  
 Dieser Testfall konzentriert sich auf Lösungen zur Versionskontrolle hinzufügen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Fügen Sie Lösung mit einer Client\-Projekt zur Versionskontrolle hinzu|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie die Projektmappe zur Versionskontrolle \(**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Versionskontrolle hinzufügen**\).|Datenquellen\-Steuerelement wurde der Projektmappe oder eines Projekts hinzugefügt.|  
|Hinzufügen von Projektmappen, die mit einem Dateisystem oder lokalen IIS\-Webprojekt an Datenquellen\-Steuerelement|1.  Ein Dateisystem oder lokalen IIS\-Webprojekt zu erstellen \(Schaltfläche "Durchsuchen" zum Verweisen auf den Projektspeicherort; Verwenden des Pfads bestimmt, welche Art von Web\-Projekt erstellt wird\).<br />2.  Fügen Sie die Projektmappe zur Versionskontrolle \(**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Versionskontrolle hinzufügen**\).|Datenquellen\-Steuerelement wurde der Projektmappe oder eines Projekts hinzugefügt.|  
|Fügen Sie die Projektmappe mit einem Remote\-Website Webprojekt an Datenquellen\-Steuerelement|1.  Erstellen Sie ein Webprojekt für Remote\-Website.<br />2.  Fügen Sie die Projektmappe zur Versionskontrolle \(**Datei**, **Quellcodeverwaltung**, **Projektmappe zur Versionskontrolle hinzufügen**\).<br />3.  Klicken Sie auf **OK** im Dialogfeld "Warnung" FrontPage\-Zugriff.|Datenquellen\-Steuerelement wurde der Projektmappe hinzugefügt.<br /><br /> Remote\-Websiteprojekt ist nicht in einem Quellcodeverwaltungsprojekt. \(Remote\-Website\-Projekten müssen von ihrem eigenen IIS\-Server gesteuert werden.\)|  
|Fügen Sie eine einzelne Projektmappe mit Source Control **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**.|1.  Erstellen Sie eine einzelne Projektmappe.<br />2.  Nur Projektmappe zur Versionskontrolle als Auswahl hinzufügen \(**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**\). Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />3.  Hinzufügen des Projekts zur Versionskontrolle als Auswahl \(**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen**\).<br />4.  Klicken Sie auf **Ja** am gleichen Speicherort des Projekts hinzu.<br />5.  Klicken Sie auf **Auschecken** in **Auschecken zum Bearbeiten** \(Dialogfeld\).|`Result from Step 2:`<br /><br /> Das Projekt und alle Dateien innerhalb des Projekts einen aktivierten, Source Control Indikator und eine QuickInfo "nicht unter quellcodeverwaltung".<br /><br /> `Result from Step 5:`<br /><br /> Projekt\-und Projektmappendatei befinden sich in demselben Ordner im Datenquellen\-Steuerelement.|  
|Brechen Sie das Hinzufügen einer Projektmappe zur Versionskontrolle|1.  Erstellen Sie eine einzelne Projektmappe.<br />2.  Versucht, das Projekt und Projektmappe zur Versionskontrolle hinzufügen. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />3.  Abbrechen Sie, nachdem Sie sich im Quellcode\-Verwaltungssystem befinden.|`Result from Step 2:`<br /><br /> Das Dialogfeld Satz Projekt Speicherort Datenquellen\-Steuerelement wird nur einmal angezeigt.<br /><br /> `Result from Step 3:`<br /><br /> Projekt hinzufügen wurde abgebrochen, Projekt\/Projektmappe befindet sich nicht unter dem Datenquellen\-Steuerelement und alle hinzufügen Source Control Menüs weiterhin verfügbar.|  
  
### Fall 1 b. Projektmappe öffnen von Datenquellen\-Steuerelement  
 Dieser Testfall konzentriert sich auf das Öffnen von Projektmappen aus Datenquellen\-Steuerelement.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Öffnen Sie eine Projektmappe, die ein Clientprojekt aus Datenquellen\-Steuerelement enthält.|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus Datenquellen\-Steuerelement an eine neue Position.|Projektmappe oder eines Projekts aus Datenquellen\-Steuerelement geöffnet.|  
|Öffnen Sie eine Projektmappe mit einem lokalen oder IIS\-Webprojekt aus Datenquellen\-Steuerelement|1.  Erstellen Sie einen lokalen oder IIS\-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus Datenquellen\-Steuerelement an eine neue Position.|Projektmappe oder eines Projekts aus Datenquellen\-Steuerelement geöffnet.|  
|Öffnen Sie eine Projektmappe mit einem Remote\-Website Webprojekt aus Datenquellen\-Steuerelement|1.  Erstellen Sie ein Webprojekt für Remote\-Website.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />3.  Schließen Sie die Projektmappe.<br />4.  Öffnen Sie die Projektmappe aus Datenquellen\-Steuerelement an eine neue Position.|`Result from Step 2:`<br /><br /> Website\-Remotewebsite ist nicht in einem Quellcodeverwaltungsprojekt.<br /><br /> `Result from Step 4:`<br /><br /> Die Lösung von Datenquellen\-Steuerelement geöffnet.<br /><br /> Remote\-Websiteprojekt wird geladen, aber es ist nicht in einem Quellcodeverwaltungsprojekt.|  
  
### Fall 1c: Hinzufügen von Projektmappen aus Datenquellen\-Steuerelement  
 Dieser Testfall konzentriert sich auf das Hinzufügen von Projektmappen aus Datenquellen\-Steuerelement.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Leere Projektmappe hinzufügen – eine einzelne Projektmappe|1.  Erstellen Sie eine einzelne Projektmappe.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine zweite leere Projektmappe.<br />5.  Fügen Sie die zuvor kontrollierte Lösung aus Datenquellen\-Steuerelement \(**Datei**, **Source Control**, **Add Project from Source Control**\).|Das hinzugefügte Projekt wird im **Projektmappen\-Explorer** und eingecheckt wird.|  
|Lösung mit einzelnen Projekt hinzufügen – Projekt|1.  Erstellen Sie eine Lösung mit einem einzelnen Projekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine zweite leere Projektmappe.<br />5.  Fügen Sie die zuvor kontrollierte Lösung aus Datenquellen\-Steuerelement \(**Datei**, **Source Control**, **Add Project from Source Control**\).|Das hinzugefügte Projekt wird im **Projektmappen\-Explorer** und eingecheckt wird.|  
|Zu Projektmappe hinzufügen – Projektmappe durch Auswahl zur Versionskontrolle hinzugefügt|1.  Erstellen einer Projektmappe ein Projekt.<br />2.  Fügen Sie nur Projektmappe zur Versionskontrolle hinzu, wie Auswahl. Wenn dieser Schritt erfolgreich ausgeführt wurde, Weiter mit nächstem Schritt.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie eine neue Projektmappe.<br />5.  Fügen Sie die zuvor kontrollierte Lösung aus Datenquellen\-Steuerelement \(**Datei**, **Source Control**, **Add Project from Source Control**\).|`Result from Step 2:`<br /><br /> Projekt ist nicht in einem Quellcodeverwaltungsprojekt.<br /><br /> `Result from Step 5:`<br /><br /> Wäre die erste Lösung Projektmappenelemente, können sie aus Datenquellen\-Steuerelement, hinzugefügt werden, damit sie nicht angezeigt werden.<br /><br /> Projekt aus erste Lösung wird als nicht verfügbar angezeigt.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)