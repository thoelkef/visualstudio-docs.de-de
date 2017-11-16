---
title: "IntelliSense für R-Code Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 821f92f7a3cf0e5ca1d647890602ec17e580b36b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense stellt Informationen über Funktionen, die Sie aufrufen können, Member von Objekten, Funktionsargumenten und [Codeausschnitte](code-snippets.md) direkt in Ihrem Blickfeld dar, wenn Sie Code schreiben. Das Feature zeigt auch mögliche Vervollständigungen an, während Sie tippen, und wird beendet, wenn Sie die TAB- oder EINGABETASTE drücken (siehe [Editor-Optionen](code-editing.md#editor-options) für die Registerkarte **Erweitert**). IntelliSense steht sowohl im Editor als auch im [interaktiven Fenster](interactive-repl.md) zur Verfügung.

![IntelliSense, das eine Funktionssignatur zeigt](media/intellisense-function-signature.png) 

Wenn Sie eine Funktion oder eine andere Anweisung eingeben, stellt IntelliSense ein Menü zur automatischen Vervollständigung bereit, das (die Groß-/Kleinschreibung beachtend) nach dem filtert, was Sie bereits eingegeben haben:

![IntelliSense-Menü für automatische Vervollständigung](media/intellisense-auto-complete-menu.png)

Das Drücken der TAB-Taste (oder der EINGABETASTE bzw. der Leertaste, je nachdem wie Optionen festgelegt sind) fügt das im Dropdownfeld ausgewählte Element ein. Sie können die Auswahl mit den Pfeiltasten ändern. 

IntelliSense bietet auch Vorschläge für Member von R-Objekten:
 
![IntelliSense-Vorschläge für Objektmember](media/intellisense-auto-complete-r-objects.png)
 
Durch Drücken der ESC-TASTE wird das gesamte Menü geschlossen. Sie können es mit der Tastenkombination STRG+Leertaste wieder öffnen.

Wenn Sie die öffnende `(` für einen Funktionsaufruf eintippen, wird die schließende `)` eingefügt, und die Signaturhilfe wird wie zuvor gezeigt aufgerufen:

![IntelliSense-Signaturhilfe für eine Funktion](media/intellisense-function-signature.png)

Über die ESC-TASTE wird das Popup-Fenster erneut geschlossen; Sie können es für Funktionsignaturen erneut mit der Tastenkombination STRG+Shift+Leertaste öffnen.

> [!Tip]
> Wenn die Parameterhilfe den darunterliegenden Text verdeckt, drücken Sie die STRG-TASTE, und halten Sie sie gedrückt. Dann wird der Text der Parameterhilfe transparent.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense für benutzerdefinierte Funktionen und Variablen

IntelliSense wird für benutzerdefinierte Funktionen in der gleichen Datei angewendet, einschließlich der Abschluss Name-Parameter:

![IntelliSense für benutzerdefinierte Funktionen](media/intellisense-same-file-functions.png)

![IntelliSense Parameterabschluss für benutzerdefinierte Funktionen](media/intellisense-parameter-completion.png)

IntelliSense gilt auch für Variablen in der gleichen Datei und der aktuellen Sitzung:

![IntelliSense Variablenabschluss](media/intellisense-variable-completion.png)

> [!Note]
> Im interaktiven Fenster berücksichtigt IntelliSense nur Namen in der aktuellen R-Sitzung und ignoriert Dateien in Ihrem Projekt.

## <a name="code-suggestions"></a>Vorschläge für Code

Wenn eine Glühbirne (Smarttag genannt) im Rand erscheint, weist Visual Studio darauf hin, dass für eine häufig verwendete Aktion eine Verknüpfung verfügbar ist. Zeigen Sie z.B. mit dem Mauszeiger auf eine Zeile, die eine `library`-Anweisung im Editor enthält. Dann sehen Sie einen Glühbirne. Wenn Sie die Glühbirne auswählen, werden die verfügbaren Optionen angezeigt:

![Smarttags für R im Editor](media/intellisense-smart-tags.png)
