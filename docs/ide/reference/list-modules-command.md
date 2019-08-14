---
title: Befehl "Module auflisten"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89be89bb3befa6f6ab9e67f6e98ae4d7b1b94e64
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926203"
---
# <a name="list-modules-command"></a>Befehl "Module auflisten"
Listet die Module für den aktuellen Prozess auf.

## <a name="syntax"></a>Syntax

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parameter
/Address:`yes|no`

Optional. Gibt an, ob die Speicheradressen der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Name:`yes|no`

Optional. Gibt an, ob die Namen der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Order:`yes|no`

Optional. Gibt an, ob die Reihenfolge der Module angezeigt werden soll. Der Standardwert ist `no`sein.

/Path:`yes|no`

Optional. Gibt an, ob die Pfade zu den Modulen angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Process:`yes|no`

Optional. Gibt an, ob die Prozesse der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

/SymbolFile:`yes|no`

Optional. Gibt an, ob die Symboldateien der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

/SymbolStatus:`yes|no`

Optional. Gibt an, ob die Symbolstatus der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

/Timestamp:`yes|no`

Optional. Gibt an, ob der Zeitstempel der Module angezeigt werden soll. Der Standardwert ist `no`sein.

/Version:`yes|no`

Optional. Gibt an, ob die Versionen der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

## <a name="example"></a>Beispiel
In diesem Beispiel werden die Modulnamen, -adressen und -zeitstempel für den aktuellen Prozess aufgeführt.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Vorgehensweise: Verwenden des Modulfensters](../../debugger/how-to-use-the-modules-window.md)