---
title: Befehl „In Dateien ersetzen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d5088366548c9f92d04f1b65a3afc378db29d6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665608"
---
# <a name="replace-in-files-command"></a>Befehl "In Dateien ersetzen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ersetzt Text in Dateien mit einem Teil der Optionen, die auf der Registerkarte **In Dateien ersetzen** im Fenster **Suchen und Ersetzen** verfügbar sind.

## <a name="syntax"></a>Syntax

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumente
 `findwhat` ist erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

 `replacewith` ist erforderlich. Der Text, durch den der übereinstimmende Text ersetzt werden soll

## <a name="switches"></a>Schalter
 /All oder/a ist optional. Ersetzt den Suchtext bei jedem Vorkommen durch den Ersetzungstext

 /case oder /c ist optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen mit den im `findwhat`-Argument angegebenen übereinstimmen.

 /ext: `extensions` ist optional. Legt die Dateierweiterungen für die zu suchenden Dateien fest.

 /Keep oder/k ist optional. Gibt an, dass alle geänderten Dateien geöffnet bleiben

 /lookin: `searchpath` ist optional. Das zu durchsuchende Verzeichnis. Wenn der Pfad Leerzeichen enthält, schließen Sie ihn vollständig in Anführungszeichen ein.

 /options oder /t ist optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

 /regex oder /r ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset oder /e ist optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

 /stop ist optional. Hält den aktuellen Suchvorgang an, wenn ein solcher ausgeführt wird. „In Dateien ersetzen“ ignoriert alle anderen Argumente, wenn `/stop` angegeben wurde. Um z.B. die aktuelle Ersetzung zu beenden, müssten Sie Folgendes eingeben:

```
>Edit.ReplaceinFiles /stop
```

 /sub oder /s ist optional. Durchsucht die Unterordner im Verzeichnis, das im Argument /lookin:`searchpath` angegeben wurde.

 /text2 oder /2 ist optional. Zeigt die Ergebnisse der Ersetzung im Fenster **Suchergebnisse 2** an.

 /wild oder /l ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

 /word oder /w ist optional. Sucht nur nach ganzen Wörtern

## <a name="example"></a>Beispiel
 In diesem Beispiel wird nach `btnCancel` gesucht. Danach werden alle CLS Dateien durch `btnReset` ersetzt, die sich im Ordner „My Visual Studio Projects“ (Meine Visual Studio-Projekte) befinden, und Informationen zu Ersetzung werden im Fenster **Suchergebnisse: 2** angezeigt.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Weitere Informationen
 Suchen [und Ersetzen von Text](../../ide/finding-and-replacing-text.md) [Ersetzung in Dateien](../../ide/replace-in-files.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) Visual Studio- [Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
