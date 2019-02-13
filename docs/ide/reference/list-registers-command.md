---
title: Befehl "Registrierungen auflisten"
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1a2361534f167a0b88b3f1b5b38c005915243d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934470"
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

 Zeigt die Werte des angegebenen `register` oder `registerGroup` an. Wenn weder `register` noch `registerGroup` angegeben ist, wird die Standardregisterliste angezeigt. Wenn kein Schalter angegeben ist, ist das Verhalten identisch. Beispiel:

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
- [Debuggrundlagen: Registerfenster](../../debugger/debugging-basics-registers-window.md)
- [Vorgehensweise: Verwenden des Fensters „Register“](../../debugger/how-to-use-the-registers-window.md)