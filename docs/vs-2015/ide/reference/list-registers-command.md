---
title: Befehl „Register auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659497"
---
# <a name="list-registers-command"></a>Befehl "Registrierungen auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt den Wert des ausgewählten Registers an und ermöglicht es Ihnen, die Liste der anzuzeigenden Register zu ändern

## <a name="syntax"></a>Syntax

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Schalter
 /Display [{ `register`&#124;`registerGroup` }...] Zeigt die Werte des angegebenen oder des an `register` `registerGroup` . Wenn weder `register` noch `registerGroup` angegeben ist, wird die Standardregisterliste angezeigt. Wenn kein Schalter angegeben ist, ist das Verhalten identisch. Beispiel:

 `Debug.ListRegisters /Display eax`

 für die folgende Syntax:

 `Debug.ListRegisters eax`

 /List zeigt alle Register Gruppen in der Liste an.

 /Watch [{ `register`&#124;`registerGroup` }...] Fügt der Liste einen oder mehrere- `register` oder- `registerGroup` Werte hinzu.

 /Unwatch [{ `register`&#124;`registerGroup` }...] Entfernt einen oder mehrere- `register` oder- `registerGroup` Werte aus der Liste.

## <a name="remarks"></a>Bemerkungen
 Der Alias `r` kann anstelle von `Debug.ListRegisters` verwendet werden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird das `Debug.ListRegisters`-Alias `r` verwendet, um die Werte der Registergruppe `Flags` anzuzeigen.

```
r /Display Flags
```

## <a name="see-also"></a>Weitere Informationen
 [Grundlagen zum Debuggen](../../debugger/debugging-basics-registers-window.md) von [Visual Studio-Befehlen](../../ide/reference/visual-studio-commands.md) : Register Fenster Gewusst [wie: Verwenden des Register Fensters](../../debugger/how-to-use-the-registers-window.md)
