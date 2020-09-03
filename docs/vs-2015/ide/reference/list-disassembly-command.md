---
title: Befehl „Disassembly auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672741"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen.

## <a name="syntax"></a>Syntax

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Schalter
 Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

 /count: `number` [oder]/c: `number` [oder]/length: `number` [oder]/l: `number` optional. Anzahl der anzuzeigenden Anweisungen. Der Standardwert ist 8.

 /EndAddress: `expression` [oder]/e: `expression` optional. Adresse, an der die Disassemblierung beendet wird.

 /Codebytes: `yes`&#124;`no` [oder]/bytes: `yes`&#124;`no` [oder]/b: `yes`&#124;`no` optional. Gibt an, ob Codebytes angezeigt werden sollen. Der Standardwert ist `no`sein.

 /Source: `yes`&#124;`no` [oder]/s: `yes`&#124;`no` optional. Gibt an, ob Quellcode angezeigt werden soll. Der Standardwert lautet `no`.

 /SymbolNames: `yes`&#124;`no` [oder]/names: `yes`&#124;`no` [oder]/n: `yes`&#124;`no` optional. Gibt an, ob Symbolnamen angezeigt werden sollen. Der Standardwert ist `yes`sein.

 [/linenumbers: `yes`&#124;`no` ] ist optional. Ermöglicht das Anzeigen von dem Quellcode zugeordneten Zeilennummern. Der Schalter „/source“ muss den Wert `yes` haben, um den Schalter „/linenumbers“ zu verwenden.

## <a name="example"></a>Beispiel

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Weitere Informationen
 Liste der Befehle zum [Auflisten der Befehls](../../ide/reference/list-call-stack-command.md) [Liste Thread Befehl](../../ide/reference/list-threads-command.md) Befehlsfenster für [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
