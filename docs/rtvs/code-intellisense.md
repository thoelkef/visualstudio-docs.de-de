---
title: "IntelliSense für R-Code Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 359b9dc6bae84bb6d89e5f0f646c0b8fed5898ec
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense stellt Informationen über Funktionen, die Sie aufrufen können, Member von Objekten, Funktionsargumenten und [Codeausschnitte](code-snippets.md) direkt auf Ihrer Sehlinie dar, wenn Sie Code schreiben. Das Feature zeigt auch mögliche Vervollständigungen an, während Sie tippen, und wird beendet, wenn Sie die TAB- oder EINGABETASTE drücken (siehe [Editor-Optionen](code-editing.md#editor-options) für die Registerkarte **Erweitert**). IntelliSense steht sowohl im Editor als auch im [interaktiven Fenster](interactive-repl.md) zur Verfügung.

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
> Wenn Sie der Meinung sind, dass der Text der Parameterhilfe versteckt ist – wie es im Datei-Editor vorkommen kann – können Sie STRG gedrückt halten, um den Text der Parameterhilfe durchscheinen zu lassen.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense für benutzerdefinierte Funktionen und Variablen

IntelliSense wird für benutzerdefinierte Funktionen in der gleichen Datei angewendet, einschließlich der Abschluss Name-Parameter:

![IntelliSense für benutzerdefinierte Funktionen](media/intellisense-same-file-functions.png)

![IntelliSense Parameterabschluss für benutzerdefinierte Funktionen](media/intellisense-parameter-completion.png)

IntelliSense gilt auch für Variablen in der gleichen Datei und der aktuellen Sitzung:

![IntelliSense Variablenabschluss](media/intellisense-variable-completion.png)

> [!Note]
> Im interaktiven Fenster berücksichtigt IntelliSense nur Namen in der aktuellen R-Sitzung und ignoriert Dateien in Ihrem Projekt.

## <a name="code-suggestions"></a>Vorschläge für Code

Wenn eine Glühbirne (Smarttag genannt) im Rand erscheint, weist Visual Studio darauf hin, dass für eine häufig verwendete Aktion eine Verknüpfung verfügbar ist. Wenn Sie z.B. mit dem Mauszeiger auf eine Zeile zeigen, die eine `library`-Anweisung im Editor enthält, und Sie eine Glühbirne sehen. Wenn Sie die Glühbirne auswählen, werden die verfügbaren Optionen angezeigt:

![Smarttags für R im Editor](media/intellisense-smart-tags.png)

