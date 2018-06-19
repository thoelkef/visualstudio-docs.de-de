---
title: Aktuellen Prozess festlegen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64561db59cc089d9539ab396cf4e869e92fe1117
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705085"
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
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)