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
ms.openlocfilehash: 18473fbd8ee0f7c4b415880da61c86de0bae6fc5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925971"
---
# <a name="toggle-breakpoint-command"></a>Befehl "Haltepunkt ein/aus"
Schaltet den Haltepunkt entweder ein oder aus, je nach seinem aktuellen Status an der aktuellen Position in der Datei.

## <a name="syntax"></a>Syntax

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumente

`text`\
Optional. Wenn Text angegeben ist, wird die Zeile als benannter Haltepunkt markiert. Andernfalls wird die Zeile als unbenannter Haltepunkt markiert. Ähnliches geschieht, wenn Sie F9 drücken.

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