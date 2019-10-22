---
title: Optionen, Text-Editor, JavaScript, Formatierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dcfa4a2fb15ed8f4abfff24aa8e78c2b08eb8412
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662250"
---
# <a name="options-text-editor-javascript-formatting"></a>Optionen, Text-Editor, JavaScript, Formatierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die Seite **Formatierung** im Dialogfeld **Optionen**, um Optionen zur Formatierung von Code im Code-Editor festzulegen. Öffnen Sie diese Seite, indem Sie auf der Menüleiste auf **Extras** und **Optionen** klicken und anschließend **Text-Editor**, **JavaScript** und **Formatierung** erweitern.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="automatic-formatting"></a>Automatische Formatierung
 Diese Optionen bestimmen, wann die Formatierung in der **Quellansicht** vorgenommen wird.

## <a name="uielement-list"></a>UIElement-Liste

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Abgeschlossene Zeile durch Eingabe formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor nach Drücken der EINGABETASTE automatisch die Zeile.|
|**Abgeschlossene Anweisung bei ";" formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor nach Drücken der SEMIKOLONTASTE automatisch die Zeile.|
|**Abgeschlossenen Block bei "}" formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor nach Drücken der schließenden geschweiften Klammer automatisch die Zeile.|
|**Beim Einfügen formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code-Editor den Code beim Einfügen in den Editor erneut. Der Editor verwendet die aktuell definierten Formatierungsregeln. Wenn diese Option nicht ausgewählt ist, verwendet der Editor die ursprüngliche Formatierung des eingefügten Codes.|

## <a name="new-lines"></a>Neue Zeilen
 Diese Optionen bestimmen, ob der Code-Editor eine öffnende geschweifte Klammer für Funktionen und Kontrollblöcke in einer neuen Zeile einfügt.

## <a name="uielement-list"></a>UIElement-Liste

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Öffnende geschweifte Klammer für Funktionen in neuer Zeile platzieren**|Wenn diese Option ausgewählt ist, verschiebt der Code-Editor die mit einer Funktion verknüpfte öffnende geschweifte Klammer in eine neue Zeile.|
|**Öffnende geschweifte Klammer für Kontrollblöcke in neuer Zeile platzieren**|Wenn diese Option ausgewählt ist, verschiebt der Code-Editor die mit einem Kontrollblock verknüpfte öffnende geschweifte Klammer (z. B. `if`- und `while`-Kontrollblöcke) in eine neue Zeile.|

## <a name="spacing"></a>Abstand
 Diese Optionen bestimmen, wie Leerzeichen in die **Quellansicht** eingefügt werden.

## <a name="uielement-list"></a>UIElement-Liste

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Leerzeichen nach Trennzeichen einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen nach einem Kommatrennzeichen eingefügt.|
|**In for-Anweisung Leerzeichen nach Semikolon einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor hinter jedem Semikolon in der ersten Zeile einer `for`-Schleife ein Leerzeichen eingefügt.|
|**Leerzeichen vor und nach binären Operatoren einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen vor und nach einem binären Operator (z.B. +, -, &&, &#124;&#124;) eingefügt.|
|**Leerzeichen nach Schlüsselwörtern in Anweisungen für die Ablaufsteuerung einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor in Anweisungen für die Ablaufsteuerung ein Leerzeichen nach JavaScript-Schüsselwörtern eingefügt.|
|**Leerzeichen nach function-Schlüsselwort für anonyme Funktionen einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen hinter dem `function`-Schlüsselwort für anonyme Funktionen eingefügt.|
|**Leerzeichen nach öffnender und vor schließender nicht leerer Klammer einfügen**|Wenn diese Option ausgewählt ist, wird im Code-Editor ein Leerzeichen hinter die öffnende Klammer und vor der schließenden Klammer eingefügt, sofern nicht leere Zeichen innerhalb der Klammern vorhanden sind.|

## <a name="see-also"></a>Siehe auch
 [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
