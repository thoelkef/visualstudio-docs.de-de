---
title: Befehl "Suchen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab914d62053b5cbefe92ee0ce8356c10dad82e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748763"
---
# <a name="find-command"></a>Befehl "Suchen"
Durchsucht Dateien mit einem Teil der Optionen, die auf der Registerkarte **In Dateien suchen** im Fenster **Suchen und Ersetzen** verfügbar sind.

## <a name="syntax"></a>Syntax

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumente
`findwhat` ist erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

## <a name="switches"></a>Schalter
/case oder /c\
Optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen den im `findwhat`-Argument angegebenen Zeichen entsprechen.

/doc oder /d\
Optional. Sucht nur im aktuellen Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/markall oder /m\
Optional. Platziert einen Graphen in jeder Zeile, die eine Suchübereinstimmung im aktuellen Dokument enthält.

/open oder /o\
Optional. Sucht in allen geöffneten Dokumenten, als wären sie ein einziges Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/options oder /t\
Optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

/proc oder /p\
Optional. Sucht nur in der aktuellen Prozedur. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/reset oder /e\
Optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

/sel oder /s\
Optional. Sucht nur in der aktuellen Auswahl. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/up oder /u\
Optional. Sucht von der aktuellen Position in der Datei bis zum Anfang der Datei. Standardmäßig beginnt die Suche bei der aktuellen Position in der Datei und wird bis zum Ende der Datei ausgeführt.

/regex oder /r\
Optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

/wild oder /l\
Optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

/word oder /w\
Optional. Sucht nur nach ganzen Wörtern.

## <a name="example"></a>Beispiel
In diesem Beispiel wird eine Suche mit Berücksichtigung der Groß- und Kleinschreibung nach dem Wort „Somestring“ im aktuell ausgewählten Codeabschnitt ausgeführt.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Siehe auch

- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)