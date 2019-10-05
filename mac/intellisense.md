---
title: IntelliSense
description: Informationen zur Verwendung von IntelliSense in Visual Studio für Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 3e99c31b1ab4d12532d701e4626ac9c1aae7df56
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026569"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense bietet verschiedene Funktionen, die das Schreiben und Bearbeiten von Code verbessern. Die IntelliSense-Engine stellt beispielsweise zusätzlich zur Codevervollständigung auch Memberlisten, Parameterinformationen und QuickInfos bereit.

In Visual Studio für Mac wird IntelliSense vom Kern-Editor-Dienst bereitgestellt und in vielen Sprachen unterstützt (z. B. C#, XAML, F#, JavaScript usw.). Visual Studio für Mac bietet auch erweiterte IntelliSense-Funktionen wie die das Anzeigen von Vervollständigungen aus Bibliotheken, die noch nicht in das Projekt importiert wurden.

## <a name="code-completion"></a>Codevervollständigung

Beim Eingeben von Code in einer unterstützten Datei (z. B. C#-Codedatei) werden in einer Vervollständigungsliste gültige Vervollständigungen für die gerade eingegebene Zeichenfolge angezeigt und beim Eingeben aktualisiert. Wenn Sie den Text löschen, wird die Liste außerdem noch mal automatisch aktualisiert, um eine größere Anzahl von Möglichkeiten zum Vervollständigen der angegebenen Zeichenfolge einzuschließen. 

Das Vervollständigungsfenster bietet auch Unterstützung für das Filtern der enthaltenen Vervollständigungen nach Typ. Es ist beispielsweise möglich, die Member der Liste einzuschränken, sodass sie nur Typen wie Klassen oder Delegate repräsentieren. Dieser Filtervorgang kann entweder durch das Klicken auf ein bestimmtes Symbol, das den zu filternden Typ darstellt, oder mithilfe von Tastenkombinationen aktiviert werden, die einem bestimmten Typ entsprechen. Die Symbole, die sich unten im Vervollständigungsfenster befinden, lauten wie folgt:

| Symbol                         | name          | Stichwort    | Hotkey |
| -----------------------------|---------------| -----------|--------|
| ![Symbol „Klassen“](media/classes-icon.png)  | class         | `class`    |  ⌥C
| ![Symbol "Konstante"](media/constant-icon.png) | Konstante      | `const`    |  ⌥O
| ![Symbol „Delegieren“](media/delegate-icon.png) | delegate      | `delegate` |  ⌥D
| ![Symbol „Enumeration“](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Symbol „Ereignis“](media/event-icon.png)    | event         |            |  ⌥V
| ![Symbol "Feld"](media/fields-icon.png)   | Feld         |            |  ⌥F
| ![Symbol „Schnittstelle“](media/interface-icon.png)| interface     | `interface`|  ⌥I
| ![Symbol „Schlüsselwort“](media/keyword-icon.png)  | keyword       |            |  ⌥K
| ![Symbol „Methode“](media/method-icon.png)   | Methode        |            |  ⌥M
| ![Symbol „Namespace“](media/namespace-icon.png)| namespace     | `namespace`|  ⌥N
| ![Symbol „Eigenschaften“](media/props-icon.png)    | property      |            |  ⌥P
| ![Symbol „Ausschnitt“](media/snippet-icon.png)  | snippet       | `class`    |  ⌥S
| ![Symbol „Struktur“](media/struct-icon.png)   | Struktur     | `struct`   |  ⌥S

Wenn Sie auf eines der Symbole klicken oder die entsprechenden Hotkeys drücken, wird die Vervollständigungsliste auf die vom Filtersatz definierten Typen beschränkt.  

![Filtern nach Typen mit IntelliSense](media/intellisense-typefiltering.gif)

## <a name="show-import-items"></a>Anzeigen von Importelementen

Standardmäßig zeigt die IntelliSense-Vervollständigung nur Vervollständigungen aus Bibliotheken an, die in Ihr Projekt importiert wurden. Wenn Sie z. B. `System.Collections.Generic` nicht über `using` importiert haben, ist keine Vervollständigung für `List<>` vorhanden. Sie müssen **Show Import Items** (Importelemente anzeigen) in den Einstellungen für Visual Studio für Mac aktivieren, um Vervollständigungen aus nicht importierten Bibliotheken anzuzeigen. Diese Einstellung befindet sich unter **Einstellungen > Text-Editor > IntelliSense**:

![Anzeigen von Importelementen mit IntelliSense](media/intellisense-showimport.png)

Wenn die Option **Show Import Items** (Importelemente anzeigen) aktiviert ist, schließt die Vervollständigungsliste die noch nicht importierten Vervollständigungen ein. Wenn Sie ein Element auswählen, das einer nicht deklarierten Bibliothek entspricht, wird die `using`-Anweisung für diese Bibliothek dem Header der Codedatei automatisch hinzugefügt. Der Name der Bibliothek, zu der die Vervollständigung gehört, wird zusammen mit eben dieser aufgeführt.

![Anzeigen der Liste der Importelemente](media/intellisense-importaction.png)

## <a name="parameter-window"></a>Parameterfenster

Ein weiteres Feature von IntelliSense ermöglicht es, bei Bedarf eine Parameterliste bereitzustellen. Die Parameterliste enthält Details zu den Methodensignaturen für den aufgerufenen Code. Durch Klicken auf die NACH-OBEN- und NACH-UNTEN-TASTEN innerhalb der Signatur können Sie jede der verfügbaren Parametersignaturen durchlaufen, um die am besten für Ihre Anforderungen geeignete Parametersignatur zu ermitteln. Zusätzlich zu den Details bezüglich der zulässigen Datentypen kann wie in der Zielmethode über XML-Kommentare definiert auch eine Beschreibung enthalten sein.

![Parameterliste](media/intellisense-parameter.png)

Wenn Sie die Parameter ausfüllen, wird der gerade bearbeitete Parameter fett formatiert, während die inaktiven Parameter die Standardgewichtung aufweisen. 


## <a name="triggering-completion-window-and-parameter-window"></a>Auslösen des Vervollständigungsfensters und des Parameterfensters

Das Vervollständigungsfenster wird bei Eingaben in der Quelldatei automatisch ausgelöst. Sie können das Vervollständigungsfenster jedoch auch mithilfe der Verknüpfung `control-space` auslösen. Diese Tastenkombination bewirkt, dass die Vervollständigungsliste an der aktuellen Position des Caretzeichens angezeigt wird. 

Sie können die Darstellung des Parameterfensters auch manuell auslösen, indem Sie `control-shift-space` eingeben. Wenn Sich das Caretzeichen an einer für die Parameterliste gültigen Position befindet, wird die Parameterliste in der Nähe der Position des Caretzeichens angezeigt.

## <a name="see-also"></a>Siehe auch

- [Schnellaktionen (Visual Studio unter Windows)](/visualstudio/ide/quick-actions)
- [Umgestalten von Code (Visual Studio unter Windows)](/visualstudio/ide/refactoring-in-visual-studio)
