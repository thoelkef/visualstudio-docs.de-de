---
title: Dokumente, Umgebung, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 705b1a5992d1a3e7931c316c713d46e7e8c7f72e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657773"
---
# <a name="documents-environment-options-dialog-box"></a>Dokumente, Umgebung, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie diese Seite des Dialogfelds **Optionen**, um die Anzeige von Dokumenten in der integrierten Entwicklungsumgebung (IDE) zu steuern und externe Änderungen an Dokumenten und Dateien zu verwalten. Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf **Optionen** klicken, und anschließend auf dem Knoten **Umgebung** **Dokumente** auswählen. Wenn **Dokumente** nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

> [!NOTE]
> Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Gespeichertes aktives Dokumentfenster wiederverwenden:** Wenn diese Option aktiviert ist, wird Ihr aktuelles Dokument geschlossen, falls es bereits gespeichert wurde, und ein neues Dokument wird im selben Fenster geöffnet. Wenn das aktuelle Dokument noch nicht gespeichert wurde bleibt es geöffnet. Das neue Dokument wird in einem separaten Fenster geöffnet. Wenn diese Option deaktiviert ist, werden neue Dokumente immer in separaten Fenstern geöffnet.

 Wenn Sie selten Ausschneide- und Einfügevorgänge in mehreren Dokumenten vornehmen und die Anzahl der geöffneten Dokumente und Fenster in Ihrem Arbeitsspeicher minimieren möchten, sollten Sie diese Option ausprobieren.

 **Ermitteln, ob eine Datei außerhalb der Umgebung geändert wird:** Wenn diese Option aktiviert ist, benachrichtigt Sie eine Meldung sofort über Änderungen an einer geöffneten Datei, die von außerhalb der IDE vorgenommen wurden. Mit dieser Meldung können Sie die Datei aus dem Speicher erneut laden.

 **Gespeicherte Änderungen automatisch laden:** Wenn die Option **Ermitteln, ob eine Datei außerhalb der Umgebung geändert wird** aktiviert ist, und eine geöffnete Datei in der IDE außerhalb der IDE geändert wird, wird standardmäßig eine Warnmeldung generiert. Wenn diese Option aktiviert ist, erscheint keine Warnung, und das Dokument wird in der IDE erneut geladen, um die externen Änderungen zu übernehmen.

 **Bearbeiten schreibgeschützter Dateien zulassen und bei Speicherversuch warnen:** Wenn diese Option aktiviert ist, können Sie schreibgeschützte Dateien öffnen und bearbeiten. Wenn Sie fertig sind, müssen Sie den Befehl **Speichern unter** ausführen, um die Datei unter einem neuen Namen zu speichern, wenn Sie einen Datensatz mit Ihren Änderungen speichern möchten.

 **Datei mit Verzeichnis des aktuellen Dokuments öffnen:** Wenn diese Option aktiviert ist, gibt sie an, dass das Dialogfeld **Datei öffnen** das Verzeichnis des aktiven Dokuments anzeigt. Wenn diese Option deaktiviert ist, zeigt das Dialogfeld **Datei öffnen** das Verzeichnis an, das zuletzt zum Öffnen einer Datei verwendet wurde.

 **Zeilenenden beim Laden auf Konsistenz überprüfen:** Aktivieren Sie diese Option, damit der Editor die Zeilenenden in einer Datei überprüft und ein Meldungsfenster anzeigt, wenn Inkonsistenzen bei der Formatierung der Zeilenenden entdeckt werden.

 **Warnen, wenn bearbeitete Dateien durch globales Rückgängigmachen geändert werden:** Aktivieren Sie diese Option zum Anzeigen eines Meldungsfeldes, wenn der Befehl **Globales Rückgängigmachen** Änderungen zurücksetzt, die bei der Umgestaltung von Dateien getroffen wurden, die nach dem Umgestaltungsvorgang ebenfalls geändert wurden. Durch das Zurücksetzen einer Datei auf den Status vor der Umgestaltung können möglicherweise Änderungen verworfen werden, die in der Datei gemacht wurden.

 **Sonstige Dateien im Projektmappen-Explorer anzeigen:** Aktivieren Sie diese Option, um den Knoten **Verschiedene Dateien** im **Projektmappen-Explorer** anzuzeigen. Verschiedene Dateien sind Dateien, die keinem Projekt oder keiner Projektmappe zugeordnet werden. Sie können aber auf Wunsch im **Projektmappen-Explorer** angezeigt werden.

> [!NOTE]
> Aktivieren Sie diese Option, um den Befehl **In Browser anzeigen** im Menü **Datei** für Webdokumente zu aktivieren, die nicht in der aktiven Webanwendung enthalten sind.

 **\<** *n* **> im Projekt „Sonstige Dateien“ gespeicherte Elemente:** Gibt die Anzahl von Dateien an, die im Ordner **Verschiedene Dateien** des **Projektmappen-Explorers** aufbewahrt werden sollen. Diese Dateien werden auch aufgelistet, wenn sie nicht mehr in einem Editor geöffnet sind. Sie können eine beliebige ganze Anzahl von 0 bis 256 angeben. Die Standardanzahl ist 0.

 Wenn Sie z.B. diese Option auf 5 festlegen, und 10 verschiedene Dateien geöffnet sind, werden die ersten 5 Dateien trotzdem noch im Ordner **Verschiedene Dateien** angezeigt, wenn Sie alle 10 Dateien schließen.

 **Dokumente als Unicode speichern, wenn Speichern der Daten in Codepage nicht möglich:** Aktivieren Sie diese Option, damit Dateien, die Informationen enthalten, die nicht mit dem ausgewählten Codepage-Standard kompatibel sind, standardmäßig als Unicode gespeichert werden.

## <a name="see-also"></a>Siehe auch
 [Dialog Feld "Umgebungsoptionen](../../ide/reference/environment-options-dialog-box.md) " [verschiedene Dateien](../../ide/reference/miscellaneous-files.md) suchen [und Ersetzen von Text](../../ide/finding-and-replacing-text.md)
