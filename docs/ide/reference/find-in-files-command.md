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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2877057f32ba6553a2cdcefbbc1bb7a8bf2884da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919254"
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
Optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen den im `findwhat`-Argument angegebenen Zeichen entsprechen.

/ext: `extensions`\
Optional. Legt die Dateierweiterungen für die zu suchenden Dateien fest. Wenn keine Erweiterung festgelegt wird und zuvor bereits eine Erweiterung angegeben wurde, wird diese verwendet.

/lookin: `searchpath`\
Optional. Das zu durchsuchende Verzeichnis. Wenn der Pfad Leerzeichen enthält, schließen Sie ihn vollständig in Anführungszeichen ein.

/names oder /n\
Optional. Zeigt eine Liste mit Dateinamen an, die Übereinstimmungen enthalten.

/options oder /t\
Optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

/regex oder /r\
Optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

/reset oder /e\
Optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

/stop\
Optional. Hält den aktuellen Suchvorgang an, wenn ein solcher ausgeführt wird. Bei der Suche werden alle anderen Argumente ignoriert, wenn `/stop` angegeben wurde. Geben Sie Folgendes ein, um z.B. die aktuelle Suche anzuhalten:

```cmd
>Edit.FindinFiles /stop
```

/sub oder /s\
Optional. Durchsucht die Unterordner im Verzeichnis, das im Argument /lookin:`searchpath` angegeben wurde.

/text2 oder /2\
Optional. Zeigt die Ergebnisse der Suche im Fenster „Suchergebnisse: 2“ an.

/wild oder /l\
Optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

/word oder /w\
Optional. Sucht nur nach ganzen Wörtern.

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