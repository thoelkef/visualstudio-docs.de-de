---
title: Befehl „Suchen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657682"
---
# <a name="find-command"></a>Befehl "Suchen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durchsucht Dateien mit einem Teil der Optionen, die auf der Registerkarte **In Dateien suchen** im Fenster **Suchen und Ersetzen** verfügbar sind.

## <a name="syntax"></a>Syntax

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumente
 `findwhat` ist erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

## <a name="switches"></a>Schalter
 /case oder /c ist optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen den im `findwhat`-Argument angegebenen Zeichen entsprechen.

 /doc oder /d ist optional. Sucht nur im aktuellen Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /markall oder /m ist optional. Platziert einen Graphen in jeder Zeile, die eine Suchübereinstimmung im aktuellen Dokument enthält.

 /open oder /o ist optional. Sucht in allen geöffneten Dokumenten, als wären sie ein einziges Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /options oder /t ist optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

 /proc oder /p ist optional. Sucht nur in der aktuellen Prozedur. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /reset oder /e ist optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

 /sel oder /s ist optional. Sucht nur in der aktuellen Auswahl. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /up oder /u ist optional. Sucht von der aktuellen Position in der Datei bis zum Anfang der Datei. Standardmäßig beginnt die Suche bei der aktuellen Position in der Datei und wird bis zum Ende der Datei ausgeführt.

 /regex oder /r ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

 /wild oder /l ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

 /word oder /w ist optional. Sucht nur nach ganzen Wörtern

## <a name="example"></a>Beispiel
 In diesem Beispiel wird eine Suche mit Berücksichtigung der Groß- und Kleinschreibung nach dem Wort „Somestring“ im aktuell ausgewählten Codeabschnitt ausgeführt.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Weitere Informationen
 [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
