---
title: Befehl „Ersetzen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665630"
---
# <a name="replace-command"></a>Befehl "Ersetzen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ersetzt Text in Dateien mit einem Teil der Optionen, die auf der Registerkarte **In Dateien ersetzen** im Fenster **Suchen und Ersetzen** verfügbar sind.

## <a name="syntax"></a>Syntax

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumente
 `findwhat` ist erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

 `replacewith` ist erforderlich. Der Text, durch den der übereinstimmende Text ersetzt werden soll

## <a name="switches"></a>Schalter
 /All oder/a ist optional. Ersetzt den Suchtext bei jedem Vorkommen durch den Ersetzungstext

 /case oder /c ist optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen mit den im `findwhat`-Argument angegebenen übereinstimmen.

 /doc oder /d ist optional. Sucht nur im aktuellen Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /Hidden oder/h ist optional. Sucht nach ausgeblendetem und reduziertem Text, z.B. nach den Metadaten eines Designzeit-Steuerelements, einem ausgeblendeten Bereich in einem umrissenen Dokument oder einer reduzierten Klasse bzw. Methode

 /open oder /o ist optional. Sucht in allen geöffneten Dokumenten, als wären sie ein einziges Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /options oder /t ist optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

 /proc oder /p ist optional. Sucht nur in der aktuellen Prozedur. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /regex oder /r ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset oder /e ist optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

 /sel oder /s ist optional. Sucht nur in der aktuellen Auswahl. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

 /up oder /u ist optional. Sucht von der aktuellen Position in der Datei bis zum Anfang der Datei. Standardmäßig beginnt die Suche bei der aktuellen Position in der Datei und wird bis zum Ende der Datei ausgeführt.

 /wild oder /l ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

 /word oder /w ist optional. Sucht nur nach ganzen Wörtern.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird `btnSend` in allen geöffneten Dokumenten durch `btnSubmit` ersetzt.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Siehe auch
 Suchen [und Ersetzen von Text](../../ide/finding-and-replacing-text.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) Visual Studio- [Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
