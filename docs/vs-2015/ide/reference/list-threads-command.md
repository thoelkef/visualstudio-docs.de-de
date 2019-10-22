---
title: Befehl „Threads auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671143"
---
# <a name="list-threads-command"></a>Befehl "Threads auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt eine Liste der Threads im aktuellen Programm an.

## <a name="syntax"></a>Syntax

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumente
 `index` ist optional. Wählt einen Thread nach seinem Index als aktuellen Thread aus

## <a name="remarks"></a>Anmerkungen
 Wenn angegeben, kennzeichnet das `index`-Argument den angegebenen Thread als aktuellen Thread. Ein Sternchen (*) wird in der Liste neben dem aktuellen Thread angezeigt.

## <a name="example"></a>Beispiel

```
>Debug.ListThreads
```

## <a name="see-also"></a>Siehe auch
 [Auflisten der Befehls](../../ide/reference/list-call-stack-command.md) [Listen-Befehlsliste disassemblierungsbefehl](../../ide/reference/list-disassembly-command.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
