---
title: Befehl "Haltepunkt ein/aus"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14f4d60bcbf7c7f394d62cc881c78ef9aa51e545
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946805"
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
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)