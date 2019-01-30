---
title: Befehl "Disassemblierung auflisten"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab169dba1ab6692c0a6df8665e20d2695c7ac2c5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028748"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Schalter
 Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

 /count: `number` [oder] /c: `number` [oder] /length: `number` [oder] /l: `number`

 Dies ist optional. Anzahl der anzuzeigenden Anweisungen. Der Standardwert ist 8.

 /endaddress: `expression` [oder] /e: `expression`

 Dies ist optional. Adresse, an der die Disassemblierung beendet wird.

 /codebytes:`yes`|`no` [oder] /bytes:`yes`|`no` [oder] /b:`yes`|`no`

 Dies ist optional. Gibt an, ob Codebytes angezeigt werden sollen. Der Standardwert ist `no`sein.

 /source:`yes`|`no` [oder] /s:`yes`|`no`

 Dies ist optional. Gibt an, ob Quellcode angezeigt werden soll. Der Standardwert ist `no`sein.

 /symbolnames:`yes`|`no` [oder] /names:`yes`|`no` [oder] /n:`yes`|`no`

 Dies ist optional. Gibt an, ob Symbolnamen angezeigt werden sollen. Der Standardwert ist `yes`sein.

 [/linenumbers:`yes`|`no`]

 Dies ist optional. Ermöglicht das Anzeigen von dem Quellcode zugeordneten Zeilennummern. Der Schalter „/source“ muss den Wert `yes` haben, um den Schalter „/linenumbers“ zu verwenden.

## <a name="example"></a>Beispiel

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)