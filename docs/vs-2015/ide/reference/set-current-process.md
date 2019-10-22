---
title: Aktuellen Prozess festlegen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665469"
---
# <a name="set-current-process"></a>Aktuellen Prozess festlegen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt den angegebenen Prozess als aktiven Prozess im Debugger fest.

## <a name="syntax"></a>Syntax

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumente
 `index` ist erforderlich. Der Index des Prozesses.

## <a name="remarks"></a>Anmerkungen
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Zum Festlegen des aktiven Prozesses können Sie den Befehl `SetCurrentProcess` verwenden.

## <a name="example"></a>Beispiel

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
