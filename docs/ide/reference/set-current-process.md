---
title: Aktuellen Prozess festlegen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f139e204fe24b105c467f9698b78c1764521706c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977134"
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