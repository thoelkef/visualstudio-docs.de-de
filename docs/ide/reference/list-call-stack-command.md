---
title: Befehl "Aufrufliste auflisten"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f62852550c161566832a7ab78d4058d1d14028f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748723"
---
# <a name="list-call-stack-command"></a>Befehl "Aufrufliste auflisten"
Zeigt die aktuelle Aufrufliste an.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argumente

`index`\
Optional. Legt den aktuellen Stapelrahmen fest, und zeigt keine Ausgabe an.

## <a name="switches"></a>Schalter
Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.

/Count:`number` [oder] /C:`number`

Optional. Maximale Anzahl der anzuzeigenden Aufruflisten. Der Standardwert ist unbegrenzt.

/ShowTypes:`yes`|`no` [oder] /T:`yes`|`no`

Optional. Gibt an, ob Parametertypen angezeigt werden sollen. Der Standardwert ist `yes`sein.

/ShowNames:`yes`|`no` [oder] /N:`yes`|`no`

Optional. Gibt an, ob Parameternamen angezeigt werden sollen. Der Standardwert ist `yes`sein.

/ShowValues:`yes`|`no` [oder] /V:`yes`|`no`

Optional. Gibt an, ob Parameterwerte angezeigt werden sollen. Der Standardwert ist `yes`sein.

/ShowModule:`yes`|`no` [oder] /M:`yes`|`no`

Optional. Gibt an, ob der Modulname angezeigt werden soll. Der Standardwert ist `yes`sein.

/ShowLineOffset:`yes`|`no` [oder] /#:`yes`|`no`

Optional. Gibt an, ob der Zeilenoffset angezeigt werden soll. Der Standardwert ist `no`sein.

/ShowByteOffset:`yes`|`no` [oder] /B:`yes`|`no`

Optional. Gibt an, ob der Byte-Offset angezeigt werden soll. Der Standardwert ist `no`sein.

/ShowLanguage:`yes`|`no` [oder] /L:`yes`|`no`

Optional. Gibt an, ob die Sprache angezeigt werden soll. Der Standardwert ist `no`sein.

/IncludeCallsAcrossThreads:`yes`|`no` [oder] /I:`yes`|`no`

Optional. Gibt an, ob angegeben werden soll, ob andere Threads aufgerufen werden oder selbst aufrufen. Der Standardwert ist `no`sein.

/ShowExternalCode:`yes`|`no`

Optional. Gibt an, ob für die Aufrufliste nur Benutzercode angezeigt werden soll. Wenn die Funktion „Nur eigenen Code“ deaktiviert ist, wird der gesamte nicht benutzerseitige Code angezeigt. Wenn diese Funktion aktiviert ist, wird nicht benutzerseitiger Code als `[external]` in der Ausgabe der Aufrufliste angezeigt.

Thread:`n`

Optional. Zeigt die Aufrufliste für den Thread `n` an. Wenn kein Thread angegeben ist, wird die Aufrufliste für den aktuellen Thread angezeigt.

## <a name="remarks"></a>Anmerkungen
Änderungen an den Argumenten oder Schaltern gelten bei zukünftigen Aufrufen dieses Befehls. Wenn Sie Debug.ListCallStackby selbst ausgeben, wird die gesamte Aufrufliste angezeigt. Wenn Sie beispielsweise einen Index angeben

```cmd
Debug.ListCallStack 2
```

wird der aktuelle Stapelrahmen auf diesen Frame festgelegt (in diesem Fall auf den zweiten Frame).

Sie können diesen Befehl auch mit dem vordefinierten Alias „kb“ schreiben. Sie können beispielsweise Folgendes eingeben:

```cmd
kb 2
```

um den aktuellen Stapelrahmen auf den zweiten Frame festzulegen.

## <a name="example"></a>Beispiel

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Disassemblierung auflisten"](../../ide/reference/list-disassembly-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)