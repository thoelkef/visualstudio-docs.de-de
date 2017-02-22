---
title: "Dokumente, Umgebung, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Environment.Documents"
  - "VS.ToolsOptionsPages.Environment.Documents"
  - "VS.ToolsOptionsPag.Environment.Documents"
helpviewer_keywords: 
  - "Dokumente, Umgebung, Optionen (Dialogfeld)"
  - "Standardwerte, Verzeichnisse"
  - "Fehlermeldungen, anpassen"
  - "Dateien [Visual Studio], Standardoptionen"
  - "Dateien [Visual Basic], automatisches Laden von geänderten"
  - "Fenster, Anpassen der Umgebung"
  - "Bearbeiten im Speicher"
  - "Ordner [Visual Studio], Angeben des Speicherorts für „Datei öffnen“"
  - "Datei öffnen (Dialogfeld)"
  - "Fenster, Aktivieren der Wiederverwendung aktueller"
  - "Benachrichtigungen, geänderte Dateien"
  - "Dateien [Visual Studio], Anzeigen im Projektmappen-Explorer"
  - "Standardverzeichnisse"
  - "schreibgeschützte Dateien, bearbeiten"
  - "Optionen (Dialogfeld), Anzeigen von sonstigen Dateien"
  - "Verzeichnisse [Visual Studio], IDE-Umgebungsoptionen"
  - "Optionen (Dialogfeld), Seite „Dokumente“"
  - "Warnungen, geänderte Dateien"
  - "Projektmappen-Explorer, Anzeigen von Dateien in"
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dokumente, Umgebung, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Auf dieser Seite des Dialogfelds **Optionen** können Sie die Anzeige von Dokumenten in der integrierten Entwicklungsumgebung \(IDE\) steuern und externe Änderungen an Dokumenten und Dateien verwalten.  Zum Öffnen dieses Dialogfelds müssen Sie im Menü **Extras** auf **Optionen** klicken und dann im Knoten **Umgebung** den Eintrag **Dokumente** auswählen.  Wenn **Dokumente** nicht in der Liste angezeigt wird, wählen Sie im Dialogfeld **Optionen** den Befehl **Alle Einstellungen anzeigen** aus.  
  
> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Aktives Dokumentfenster wiederverwenden, falls gespeichert**  
 Wenn diese Option aktiviert ist, wird das aktuelle Dokument geschlossen, falls es gespeichert ist, und ein neues Dokument in demselben Fenster geöffnet.  Wenn das aktuelle Dokument nicht gespeichert wurde, bleibt es offen, und das neue Dokument wird in einem anderen Fenster geöffnet.  Wenn diese Option deaktiviert wird, werden neue Dokumente immer in gesonderten Fenstern geöffnet.  
  
 Diese Option empfiehlt sich, wenn Sie selten Inhalt aus einem Dokument ausschneiden und in ein anderes einfügen und Sie die Anzahl geöffneter Dokumente und Fenster im Arbeitsbereich minimieren möchten.  
  
 **Ermitteln, ob Datei außerhalb der Umgebung geändert wird**  
 Wenn diese Option aktiviert ist, werden Sie sofort benachrichtigt, wenn an einer geöffneten Datei in einem Editor außerhalb der IDE Änderungen vorgenommen wurden.  Die Meldung ermöglicht das erneute Laden der Datei aus dem Speicher.  
  
 **Gespeicherte Änderungen automatisch laden**  
 Wenn die Option **Ermitteln, ob Datei außerhalb der Umgebung geändert wird** aktiviert ist und eine in der IDE geöffnete Datei außerhalb der IDE geändert wird, wird standardmäßig eine Warnmeldung angezeigt.  Wenn diese Option deaktiviert ist, wird keine Warnmeldung angezeigt, und das Dokument wird neu in die IDE geladen, damit die externen Änderungen übernommen werden.  
  
 **Bearbeiten schreibgeschützter Dateien zulassen und bei Speicherversuch warnen**  
 Wenn diese Option aktiviert ist, können Sie eine schreibgeschützte Datei öffnen und bearbeiten.  Wenn Sie fertig sind, müssen Sie die  **Speichern unter**Befehl aus, um die Datei unter einem neuen Namen speichern, wenn Sie Ihre Änderungen speichern möchten.  
  
 **Datei mit Verzeichnis des aktuellen Dokuments öffnen**  
 Durch Auswahl dieser Option wird festgelegt, dass im Dialogfeld **Datei öffnen** das Verzeichnis des aktiven Dokuments angezeigt wird.  Wenn diese Option deaktiviert wird, wird im Dialogfeld **Datei öffnen** das Verzeichnis angezeigt, in dem zuletzt eine Datei geöffnet wurde.  
  
 **Zeilenenden beim Laden auf Konsistenz überprüfen**  
 Aktivieren Sie diese Option, wenn die Zeilenenden in einer Datei vom Editor überprüft und ein Meldungsfeld angezeigt werden soll, sobald eine inkonsistente Formatierung der Zeilenenden gefunden wird.  
  
 **Warnen, wenn bearbeitete Dateien durch globales Rückgängigmachen geändert werden**  
 Aktivieren Sie diese Option, damit eine Meldung angezeigt wird, wenn durch den Befehl **Global rückgängig** Umgestaltungsänderungen an Dateien zurückgesetzt werden, die nach der Umgestaltung geändert wurden.  Wenn eine Datei in den Zustand vor der Umgestaltung zurückgesetzt wird, werden möglicherweise auch Änderungen verworfen, die nachträglich an der Datei vorgenommen wurden.  
  
 **Verschiedene Dateien im Projektmappen\-Explorer anzeigen**  
 Aktivieren Sie diese Option, um im **Projektmappen\-Explorer** den Knoten **Sonstige Dateien** anzuzeigen.  Sonstige Dateien sind Dateien, die keinem Projekt bzw. keiner Projektmappe zugeordnet sind. Sie können jedoch auf Wunsch im **Projektmappen\-Explorer** angezeigt werden.  
  
> [!NOTE]
>  Aktivieren Sie mit dieser Option im Menü **Datei** den Befehl **In Browser anzeigen** für Webdokumente, die in der aktiven Webanwendung nicht enthalten sind.  
  
 **\<** *n* **\> im Projekt für verschiedene Dateien gespeicherte Elemente**  
 Gibt die Anzahl von Dateien an, die im **Projektmappen\-Explorer** im Ordner **Verschiedene Dateien** beibehalten werden sollen.  Diese Dateien werden auch dann aufgelistet, wenn sie nicht mehr in einem Editor geöffnet sind.  Sie können eine beliebige ganze Zahl von 0 bis 256 angeben.  Die Anzahl beträgt standardmäßig 0.  
  
 Wenn Sie diese Option z. B. auf 5 festlegen und 10 verschiedene Dateien geöffnet sind und Sie nun sämtliche 10 Dateien schließen, wird im Ordner **Verschiedene Dateien**  weiterhin 5 angezeigt.  
  
 **Dokumente als Unicode speichern, wenn Speichern der Daten in Codepage nicht möglich**  
 Aktivieren Sie diese Option, um Dateien mit Informationen, die mit der ausgewählten Codepage nicht kompatibel sind, standardmäßig im Unicode\-Format zu speichern.  
  
## Siehe auch  
 [Dialogfeld "Umgebungsoptionen"](../../ide/reference/environment-options-dialog-box.md)   
 [Verschiedene Dateien](../../ide/reference/miscellaneous-files.md)   
 [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)