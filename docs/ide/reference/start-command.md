---
title: Befehl "Start"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6138c4cff33f0b2a4211439a01a058da59da811
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590279"
---
# <a name="start-command"></a>Befehl "Start"
Startet das Debuggen des Startup-Projekts.

## <a name="syntax"></a>Syntax

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumente
`address`

Dies ist optional. Die Adresse, an der das Programm die Ausführung anhält, ähnlich wie ein Breakpoint im Quellcode. Dieses Argument ist nur im Debugmodus gültig.

## <a name="remarks"></a>Bemerkungen
Der Befehl **Start** führt bei der Ausführung einen RunToCursor-Vorgang auf die angegebene Adresse aus.

## <a name="example"></a>Beispiel
In diesem Beispiel wird der Debugger gestartet und ignoriert alle auftretenden Ausnahmen.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
