---
title: Befehl "In Dateien suchen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d313c29be1d5fb4f1be1febe9b5b7cd32e7e11
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569581"
---
# <a name="find-in-files-command"></a>Befehl "In Dateien suchen"
Durchsucht Dateien mithilfe einer Teilmenge der Optionen, die im Fenster **Suchen und Ersetzen** auf der Registerkarte **In Dateien suchen** verfügbar sind.

## <a name="syntax"></a>Syntax

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumente

`findwhat`\
Erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

## <a name="switches"></a>Schalter
/case oder /c\
Dies ist optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen den im `findwhat`-Argument angegebenen Zeichen entsprechen.

/ext: `extensions`\
Dies ist optional. Legt die Dateierweiterungen für die zu suchenden Dateien fest. Wenn keine Erweiterung festgelegt wird und zuvor bereits eine Erweiterung angegeben wurde, wird diese verwendet.

/lookin: `searchpath`\
Dies ist optional. Das zu durchsuchende Verzeichnis. Wenn der Pfad Leerzeichen enthält, schließen Sie ihn vollständig in Anführungszeichen ein.

/names oder /n\
Dies ist optional. Zeigt eine Liste mit Dateinamen an, die Übereinstimmungen enthalten.

/options oder /t\
Dies ist optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

/regex oder /r\
Dies ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

/reset oder /e\
Dies ist optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

/stop\
Dies ist optional. Hält den aktuellen Suchvorgang an, wenn ein solcher ausgeführt wird. Bei der Suche werden alle anderen Argumente ignoriert, wenn `/stop` angegeben wurde. Geben Sie Folgendes ein, um z.B. die aktuelle Suche anzuhalten:

```cmd
>Edit.FindinFiles /stop
```

/sub oder /s\
Dies ist optional. Durchsucht die Unterordner im Verzeichnis, das im Argument /lookin:`searchpath` angegeben wurde.

/text2 oder /2\
Dies ist optional. Zeigt die Ergebnisse der Suche im Fenster „Suchergebnisse: 2“ an.

/wild oder /l\
Dies ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

/word oder /w\
Dies ist optional. Sucht nur nach ganzen Wörtern.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird nach „btnCancel“ in allen CLS-Dateien gesucht, die sich im Ordner „My Visual Studio Projects“ (Meine Visual Studio-Projekte) befinden. Die Ergebnisse werden im Fenster „Suchergebnisse: 2“ angezeigt.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Siehe auch

- [Suchen in Dateien](../../ide/find-in-files.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
