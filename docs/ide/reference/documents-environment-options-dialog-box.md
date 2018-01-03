---
title: "Dokumente, Umgebung, Dialogfeld „Optionen“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0c89e8b018fa0979fe4c73f5cd9e0db95efd88d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="documents-environment-options-dialog-box"></a>Dokumente, Umgebung, Dialogfeld "Optionen"
Verwenden Sie diese Seite des Dialogfelds **Optionen**, um die Anzeige von Dokumenten in der integrierten Entwicklungsumgebung (IDE) zu steuern und externe Änderungen an Dokumenten und Dateien zu verwalten. Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf **Optionen** klicken, und anschließend auf dem Knoten **Umgebung** **Dokumente** auswählen. Wenn **Dokumente** nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.  
  
> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Gespeichertes aktives Dokumentfenster wiederverwenden**  
 Wenn diese Option aktiviert ist, wird Ihr aktuelles Dokument geschlossen, falls es bereits gespeichert wurde, und ein neues Dokument im selben Fenster wird geöffnet. Wenn das aktuelle Dokument noch nicht gespeichert wurde bleibt es geöffnet. Das neue Dokument wird in einem separaten Fenster geöffnet. Wenn diese Option deaktiviert ist, werden neue Dokumente immer in separaten Fenstern geöffnet.  
  
 Wenn Sie selten Ausschneide- und Einfügevorgänge in mehreren Dokumenten vornehmen und die Anzahl der geöffneten Dokumente und Fenster in Ihrem Arbeitsspeicher minimieren möchten, sollten Sie diese Option ausprobieren.  
  
 **Ermitteln, ob Datei außerhalb der Umgebung geändert wird**  
 Wenn diese Option aktiviert ist, benachrichtigt Sie eine Meldung sofort über Änderungen einer geöffneten Datei, die von außerhalb der IDE vorgenommen wurden. Mit dieser Meldung können Sie die Datei aus dem Speicher erneut laden.  
  
 **Gespeicherte Änderungen automatisch laden**  
 Wenn die Datei **Gespeicherte Änderungen automatisch laden** aktiviert ist, und eine geöffnete Datei in der IDE außerhalb der IDE geändert wird, wird standardmäßig eine Warnmeldung generiert. Wenn diese Option aktiviert ist, erscheint keine Warnung, und das Dokument wird in der IDE erneut geladen, um die externen Änderungen zu übernehmen.  
  
 **Bearbeiten schreibgeschützter Dateien zulassen und bei Speicherversuch warnen**  
 Wenn diese Option aktiviert ist, können Sie eine schreibgeschützte Datei öffnen und bearbeiten. Wenn Sie fertig sind, müssen Sie den Befehl **Speichern unter** ausführen, um die Datei unter einem neuen Namen zu speichern, wenn Sie einen Datensatz mit Ihren Änderungen speichern möchten.  
  
 **Datei mit Verzeichnis des aktuellen Dokuments öffnen**  
 Wenn diese Option aktiviert ist, gibt sie an, dass das Dialogfeld **Datei öffnen** das Verzeichnis des aktiven Dokuments anzeigt. Wenn diese Option deaktiviert ist, zeigt das Dialogfeld **Datei öffnen** das Verzeichnis an, das zuletzt zum Öffnen einer Datei verwendet wurde.  
  
 **Zeilenenden beim Laden auf Konsistenz überprüfen**  
 Aktivieren Sie diese Option, damit der Editor die Zeilenenden in einer Datei überprüft und ein Meldungsfenster anzeigt, wenn Inkonsistenzen bei der Formatierung der Zeilenenden entdeckt werden.  
  
 **Warnen, wenn bearbeitete Dateien durch globales Rückgängigmachen geändert werden**  
 Aktivieren Sie diese Option zum Anzeigen eines Meldungsfeldes, wenn der Befehl **Globales Rückgängigmachen** Änderungen zurücksetzt, die bei der Umgestaltung von Dateien getroffen wurden, die nach dem Umgestaltungsvorgang ebenfalls geändert wurden. Durch das Zurücksetzen einer Datei auf den Status vor der Umgestaltung können möglicherweise Änderungen verworfen werden, die in der Datei gemacht wurden.  
  
 **Sonstige Dateien im Projektmappen-Explorer anzeigen**  
 Aktivieren Sie diese Option, um den Knoten **Verschiedene Dateien** im **Projektmappen-Explorer** anzuzeigen. Verschiedene Dateien sind Dateien, die keinem Projekt oder keiner Projektmappe zugeordnet werden. Sie können aber auf Wunsch im **Projektmappen-Explorer** angezeigt werden.  
  
> [!NOTE]
>  Aktivieren Sie diese Option, um den Befehl **In Browser anzeigen** im Menü **Datei** für Webdokumente zu aktivieren, die nicht in der aktiven Webanwendung enthalten sind.  
  
 **\<** *n* **> im Projekt „Sonstige Dateien“ gespeicherte Elemente**  
 Gibt die Anzahl von Dateien an, die im Ordner **Verschiedene Dateien** des **Projektmappen-Explorers** aufbewahrt werden sollen. Diese Dateien werden auch aufgelistet, wenn sie nicht mehr in einem Editor geöffnet sind. Sie können eine beliebige ganze Anzahl von 0 bis 256 angeben. Die Standardanzahl ist 0.  
  
 Wenn Sie z.B. diese Option auf 5 festlegen, und 10 verschiedene Dateien geöffnet sind, werden die ersten 5 Dateien trotzdem noch im Ordner **Verschiedene Dateien** angezeigt, wenn Sie alle 10 Dateien schließen.  
  
 **Dokumente als Unicode speichern, wenn Speichern der Daten in Codepage nicht möglich**  
 Aktivieren Sie diese Option, damit Dateien, die Informationen enthalten, die nicht mit dem ausgewählten Codepage-Standard kompatibel sind, standardmäßig als Unicode gespeichert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)   
 [Verschiedene Dateien](../../ide/reference/miscellaneous-files.md)   
 [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)