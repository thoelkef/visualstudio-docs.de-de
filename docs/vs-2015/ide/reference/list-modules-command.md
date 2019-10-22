---
title: Befehl „Module auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659531"
---
# <a name="list-modules-command"></a>Befehl "Module auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Listet die Module für den aktuellen Prozess auf.

## <a name="syntax"></a>Syntax

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parameter
 /Address: `yes|no` optional. Gibt an, ob die Speicheradressen der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

 /Name:`yes|no` ist optional. Gibt an, ob die Namen der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

 /Order: `yes|no` optional. Gibt an, ob die Reihenfolge der Module angezeigt werden soll. Der Standardwert ist `no`sein.

 /Path:`yes|no` ist optional. Gibt an, ob die Pfade zu den Modulen angezeigt werden sollen. Der Standardwert ist `yes`sein.

 /Process: `yes|no` optional. Gibt an, ob die Prozesse der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

 /SymbolFile: `yes|no` optional. Gibt an, ob die Symboldateien der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

 /SymbolStatus: `yes|no` optional. Gibt an, ob die Symbolstatus der Module angezeigt werden sollen. Der Standardwert ist `yes`sein.

 /Timestamp: `yes|no` optional. Gibt an, ob der Zeitstempel der Module angezeigt werden soll. Der Standardwert ist `no`sein.

 /Version:`yes|no` ist optional. Gibt an, ob die Versionen der Module angezeigt werden sollen. Der Standardwert ist `no`sein.

## <a name="remarks"></a>Anmerkungen

## <a name="example"></a>Beispiel
 In diesem Beispiel werden die Modulnamen, -adressen und -zeitstempel für den aktuellen Prozess aufgeführt.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Siehe auch
 [Befehlsfenster](../../ide/reference/command-window.md) für [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) Gewusst [wie: Verwenden des Fensters "Module](../../debugger/how-to-use-the-modules-window.md) "
