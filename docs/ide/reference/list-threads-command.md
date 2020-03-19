---
title: Befehl "Threads auflisten"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b36b8f4d9970d94eb83c47b59e85d01f932589
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595487"
---
# <a name="list-threads-command"></a>Befehl "Threads auflisten"
Zeigt eine Liste der Threads im aktuellen Programm an.

## <a name="syntax"></a>Syntax

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumente
`index`

Dies ist optional. Wählt einen Thread nach seinem Index als aktuellen Thread aus

## <a name="remarks"></a>Bemerkungen
Wenn angegeben, kennzeichnet das `index`-Argument den angegebenen Thread als aktuellen Thread. Ein Sternchen (*) wird in der Liste neben dem aktuellen Thread angezeigt.

## <a name="example"></a>Beispiel

```
>Debug.ListThreads
```

## <a name="see-also"></a>Weitere Informationen

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Disassembly auflisten (Befehl)](../../ide/reference/list-disassembly-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
