---
title: In Dateien ersetzen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669975"
---
# <a name="replace-in-files"></a>In Dateien ersetzen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

„In Dateien ersetzen“** ermöglicht es Ihnen, den Code bestimmter Dateien nach einer Zeichenfolge oder einem Ausdruck zu durchsuchen und einige oder alle gefundenen Übereinstimmungen zu ändern. Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster Such **Ergebnisse** aufgelistet, das unter **Ergebnis Optionen**ausgewählt wurde.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Rufen Sie die Option **In Dateien ersetzen** im Fenster **Suchen und Ersetzen** mithilfe einer der folgenden Methoden auf.

### <a name="to-display-replace-in-files"></a>So zeigen Sie „In Dateien ersetzen“ an

1. Erweitern Sie im Menü **Bearbeiten** das Fenster **Suchen und Ersetzen**.

2. Wählen Sie **In Dateien ersetzen** aus.

     \- oder -

     Wählen Sie auf der Symbolleiste **In Dateien ersetzen** aus, wenn das Fenster **Suchen und Ersetzen** bereits geöffnet ist.

## <a name="find-what"></a>Suchen nach
 Um eine neue Zeichenfolge oder einen neuen Ausdruck zu suchen, geben Sie die Zeichenfolge oder den Ausdruck im Feld ein. Um nach einer der 20 Zeichenfolgen zu suchen, nach denen Sie zuletzt gesucht haben, öffnen Sie die Liste, und wählen Sie die Zeichenfolge aus, nach der Sie suchen möchten. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Ersetzen durch
 Wenn Sie Instanzen der Zeichenfolge im Feld **Suchen nach** mit einer anderen Zeichenfolge ersetzen möchten, geben Sie die neue Zeichenfolge im Feld **Ersetzen durch** ein. Lassen Sie dieses Feld leer, um Instanzen der Zeichenfolge im Feld **Suchen nach** zu löschen. Öffnen Sie die Liste, um 20 Zeichenfolgen anzuzeigen, die Sie zuletzt gesucht haben. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Ersatzzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Suchen in
 Über die aus der Dropdownliste **Suchen in** ausgewählte Option legen Sie fest, ob die Funktion **In Dateien ersetzen** nur die zurzeit aktiven Dateien oder alle in bestimmten Ordnern gespeicherten Dateien durchsucht. Wählen Sie einen Suchbereich aus der Liste aus, geben Sie einen Ordnerpfad ein, oder klicken Sie auf die Schaltfläche **Durchsuchen (...)**, um das Dialogfeld **Suchordner auswählen** aufzurufen und Ordner zum Durchsuchen auszuwählen. Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.

> [!NOTE]
> Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur eine Version der Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.

## <a name="find-options"></a>Suchoptionen
 Sie können den Abschnitt Such **Optionen** erweitern oder reduzieren. Die folgenden Optionen können aktiviert oder deaktiviert werden:

 Groß-/Kleinschreibung suchen wenn diese Option ausgewählt ist, werden im Fenster Such **Ergebnisse** nur Instanzen der Zeichenfolge **Find What** angezeigt, die sowohl nach Inhalt als auch nach Fall übereinstimmen. Beispielsweise wird eine Suche nach „MyObject“ mit der Option **Groß-/Kleinschreibung beachten** nur „MyObject“ zurückgeben, nicht „myobject“ oder „MYOBJECT“.

 Vollständiges Wort suchen wenn diese Option ausgewählt ist, werden im Fenster Such **Ergebnisse** nur Instanzen der Zeichenfolge **Find What** angezeigt, die mit vollständigen Wörtern übereinstimmen. Beispielsweise wird eine Suche nach „MyObject“ mit dieser Option „MyObject“ zurückgeben, aber nicht „CMyObject“ oder „MyObjectC“.

 Reguläre Ausdrücke verwenden Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen verwenden, um Textmuster in den Textfeldern **Suchen** nach oder **Ersetzen durch** zu definieren. Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Sehen Sie sich diese Dateitypen an. diese Liste gibt die Dateitypen an, die in den Verzeichnissen " **Suchen in** " durchsucht werden sollen. Wenn dieses Feld leer bleibt, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.

 Wählen Sie ein beliebiges Element aus der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.

## <a name="result-options"></a>Ergebnisoptionen
 Sie können den Abschnitt **Ergebnis Optionen** erweitern oder reduzieren. Die folgenden Optionen können aktiviert oder deaktiviert werden:

 Fenster Ergebnisse 1 suchen wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters Such **Ergebnisse 1** . Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.

 Fenster "Suchergebnisse 2" Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters Such **Ergebnisse 2** . Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend** Suchergebnisse: 2** aus.

 Nur Dateinamen anzeigen wenn dieses Kontrollkästchen aktiviert ist, werden im Fenster Suchergebnisse die vollständigen Namen und Pfade für alle Dateien aufgelistet, die die Such Zeichenfolge enthalten. Die Ergebnisse enthalten allerdings nicht die Codezeile, in der die Zeichenfolge vorkommt. Dieses Kontrollkästchen ist nur für „Suchen in Dateien“ verfügbar.

 Geänderte Dateien offen lassen, nachdem alles ersetzt wurde Wenn diese Option aktiviert ist, bleiben alle Dateien geöffnet, in denen Ersetzungen vorgenommen wurden. Auf diese Weise können Sie die Änderungen rückgängig machen oder speichern. Speichereinschränkungen können eine Begrenzung der Anzahl der Dateien, die nach einem Ersetzungsvorgang geöffnet bleiben, zur Folge haben.

> [!CAUTION]
> Sie können die Funktion **Rückgängig** nur bei Dateien verwenden, die zum Bearbeiten geöffnet bleiben. Wenn diese Option nicht aktiviert ist, bleiben Dateien, die nicht bereits zum Bearbeiten geöffnet waren, geschlossen, und die Option **Rückgängig** steht für diese Dateien nicht zur Verfügung.

## <a name="see-also"></a>Weitere Informationen
 Suchen [und Ersetzen von Text](../ide/finding-and-replacing-text.md) [Suchen in Dateien](../ide/find-in-files.md) [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md)
