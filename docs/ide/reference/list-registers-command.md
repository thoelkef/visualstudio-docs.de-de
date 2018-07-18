---
title: Befehl "Registrierungen auflisten"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce91abde91edf989b33c476b042abaf16c685df0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704901"
---
# <a name="list-registers-command"></a>Befehl "Registrierungen auflisten"
Zeigt den Wert des ausgewählten Registers an und ermöglicht es Ihnen, die Liste der anzuzeigenden Register zu ändern

## <a name="syntax"></a>Syntax

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Schalter
 /Display [{`register`|`registerGroup`}...]

 Zeigt die Werte des angegebenen `register` oder `registerGroup` an. Wenn weder `register` noch `registerGroup` angegeben ist, wird die Standardregisterliste angezeigt. Wenn kein Schalter angegeben ist, ist das Verhalten identisch. Zum Beispiel:

 `Debug.ListRegisters /Display eax`

 für die folgende Syntax:

 `Debug.ListRegisters eax`

 /List

 Zeigt alle Registergruppen in der Liste an

 /Watch [{`register`|`registerGroup`}...]

 Fügt der Liste einen oder mehrere `register`- oder `registerGroup`-Werte hinzu

 /Unwatch [{`register`|`registerGroup`}...]

 Entfernt einen oder mehrere `register`- oder `registerGroup`-Werte aus der Liste

## <a name="remarks"></a>Hinweise
 Der Alias `r` kann anstelle von `Debug.ListRegisters` verwendet werden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird das `Debug.ListRegisters`-Alias `r` verwendet, um die Werte der Registergruppe `Flags` anzuzeigen.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Grundlagen des Debuggens: Fenster "Register"](../../debugger/debugging-basics-registers-window.md)
- [Gewusst wie: Verwenden des Fensters "Register"](../../debugger/how-to-use-the-registers-window.md)