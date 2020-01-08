---
title: Aktuellen Prozess festlegen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3440c66d79fef3eac3744681870c9ce1ed0e97b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593550"
---
# <a name="set-current-process"></a>Aktuellen Prozess festlegen
Legt den angegebenen Prozess als aktiven Prozess im Debugger fest.

## <a name="syntax"></a>Syntax

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumente
`index`

Erforderlich. Der Index des Prozesses.

## <a name="remarks"></a>Hinweise
Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Zum Festlegen des aktiven Prozesses können Sie den Befehl `SetCurrentProcess` verwenden.

## <a name="example"></a>Beispiel

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
