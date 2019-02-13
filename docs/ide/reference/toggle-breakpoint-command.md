---
title: Befehl "Haltepunkt ein/aus"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 214897a0f938d8ea52306b8f605948b38f196111
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970464"
---
# <a name="toggle-breakpoint-command"></a>Befehl "Haltepunkt ein/aus"
Schaltet den Haltepunkt entweder ein oder aus, je nach seinem aktuellen Status an der aktuellen Position in der Datei.

## <a name="syntax"></a>Syntax

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumente
 `text` ist optional. Wenn Text angegeben ist, wird die Zeile als benannter Haltepunkt markiert. Andernfalls wird die Zeile als unbenannter Haltepunkt markiert. Ähnliches geschieht, wenn Sie F9 drücken.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der aktuelle Haltepunkt umgeschaltet.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)