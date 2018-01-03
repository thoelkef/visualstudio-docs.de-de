---
title: Finden und Ersetzen in Dateien in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 496cd3c2c6d92e5db591c09bf4d0d5ec645e4c79
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="replace-in-files"></a>In Dateien ersetzen

**In Dateien ersetzen** ermöglicht Ihnen, nach dem Code eines bestimmten Satzes von Dateien für eine Zeichenfolge oder einen Ausdruck zu suchen und einige oder alle gefundenen Übereinstimmungen zu ändern. Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster **Suchergebnisse** angezeigt, das unter **Ergebnisoptionen** ausgewählt wurde.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie auf **Extras** > **Einstellungen importieren/exportieren** und dann auf **Alle Einstellungen zurücksetzen**, um Ihre Einstellungen z.B. in **Allgemein** oder **Visual C++** zu ändern.

Rufen Sie die Option **In Dateien ersetzen** im Fenster **Suchen und Ersetzen** mithilfe einer der folgenden Methoden auf.

## <a name="to-display-replace-in-files"></a>So zeigen Sie „In Dateien ersetzen“ an

1. Erweitern Sie im Menü **Bearbeiten** das Fenster **Suchen und Ersetzen**.

1. Wählen Sie **In Dateien ersetzen** aus.

   - oder -

Wählen Sie auf der Symbolleiste **In Dateien ersetzen** aus, wenn das Fenster **Suchen und Ersetzen** bereits geöffnet ist.

## <a name="find-what"></a>Suchen nach

Um eine neue Zeichenfolge oder einen neuen Ausdruck zu suchen, geben Sie die Zeichenfolge oder den Ausdruck im Feld ein. Öffnen Sie die Dropdownliste, und wählen Sie die Zeichenfolge aus, um nach einer der 20 Zeichenfolgen zu suchen, nach denen Sie zuletzt gesucht haben. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Die Schaltfläche **Ausdrucks-Generator** wird nur aktiviert, wenn Sie in den **Suchoptionen** **Reguläre Ausdrücke verwenden** ausgewählt haben.

## <a name="replace-with"></a>Ersetzen durch

Wenn Sie Instanzen der Zeichenfolge im Feld **Suchen nach** mit einer anderen Zeichenfolge ersetzen möchten, geben Sie die neue Zeichenfolge im Feld **Ersetzen durch** ein. Lassen Sie dieses Feld leer, um Instanzen der Zeichenfolge im Feld **Suchen nach** zu löschen. Öffnen Sie die Liste, um 20 Zeichenfolgen anzuzeigen, die Sie zuletzt gesucht haben. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Ersatzzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Suchen in

Die in der Dropdownliste **Suchen in** ausgewählte Option bestimmt, ob mit der Option **In Dateien ersetzen** nur die derzeit aktiven Dateien oder alle Dateien in bestimmten Ordnern durchsucht werden. Wählen Sie einen Suchbereich aus der Liste aus, geben Sie einen Ordnerpfad ein, oder klicken Sie auf die Schaltfläche **Durchsuchen (...)**, um das Dialogfeld **Suchordner auswählen** aufzurufen und Ordner zum Durchsuchen auszuwählen. Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.

> [!NOTE]
> Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur eine Version der Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.

## <a name="find-options"></a>Suchoptionen

Der Bereich **Suchoptionen** kann erweitert oder reduziert werden. Die folgenden Optionen können aktiviert oder deaktiviert werden:

Groß-/Kleinschreibung beachten  
Wenn diese Option aktiviert ist, werden im Fenster **Suchergebnisse** nur Instanzen der Zeichenfolge aus **Suchen nach** angezeigt, bei denen sowohl der Inhalt als auch die Groß-/Kleinschreibung übereinstimmen. Beispielsweise wird eine Suche nach „MyObject“ mit der Option **Groß-/Kleinschreibung beachten** nur „MyObject“ zurückgeben, nicht „myobject“ oder „MYOBJECT“.

Nur ganzes Wort suchen  
Wenn diese Option aktiviert ist, werden im Fenster **Suchergebnisse** nur Instanzen der Zeichenfolge aus **Suchen nach** angezeigt, bei denen das ganze Wort übereinstimmt. Beispielsweise wird eine Suche nach „MyObject“ mit dieser Option „MyObject“ zurückgeben, aber nicht „CMyObject“ oder „MyObjectC“.

Reguläre Ausdrücke verwenden  
Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen zur Definition von Textmustern in den Textfeldern **Suchen nach** oder **Ersetzen durch** verwenden. Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Nach diesen Dateitypen suchen  
Diese Liste gibt Dateitypen an, die in den unter **Suchen in** angegebenen Verzeichnissen durchsucht werden sollen. Wenn dieses Feld leer bleibt, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.

Wählen Sie ein beliebiges Element aus der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.

## <a name="result-options"></a>Ergebnisoptionen

Der Bereich **Ergebnisoptionen** kann erweitert oder reduziert werden. Die folgenden Optionen können aktiviert oder deaktiviert werden:

Fenster „Suchergebnisse: 1“  
Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 1**. Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.

Fenster „Suchergebnisse: 2“  
Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 2**. Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 2** aus.

Nur Dateinamen anzeigen  
Wenn dieses Kontrollkästchen aktiviert ist, listet das Fenster „Suchergebnisse“ die vollständigen Namen und Pfade für alle Dateien auf, die die Suchzeichenfolge enthalten. Die Ergebnisse enthalten allerdings nicht die Codezeile, in der die Zeichenfolge vorkommt. Dieses Kontrollkästchen ist nur für „Suchen in Dateien“ verfügbar.

Offenlassen von geänderten Daten nach „Alle ersetzen“  
Bei Auswahl dieser Option bleiben alle Dateien geöffnet, in denen Ersetzungen vorgenommen wurden, damit Sie die Änderungen rückgängig machen oder speichern können. Einschränkungen des Speicherplatzes können die Anzahl von Dateien beeinflussen, die nach einem Ersetzungsvorgang geöffnet bleiben können.

> [!CAUTION]
> Sie können **Rückgängigmachen** nur bei Dateien anwenden, die für die Bearbeitung geöffnet bleiben. Wenn diese Option nicht ausgewählt ist, bleiben Dateien geschlossen, die nicht für die Bearbeitung geöffnet waren. Das bedeutet, dass die Option **Rückgängigmachen** in diesen Dateien nicht zur Verfügung steht.

## <a name="see-also"></a>Siehe auch

[Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)  
[Suchen in Dateien](../ide/find-in-files.md)  
[Visual Studio-Befehle](../ide/reference/visual-studio-commands.md)