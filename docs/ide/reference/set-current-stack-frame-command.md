---
title: Befehl "Aktuellen Stapelrahmen festlegen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eea69dc4d2931f66d4c6769667e23bdfb4eecf1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938286"
---
# <a name="set-current-stack-frame-command"></a>Befehl "Aktuellen Stapelrahmen festlegen"
Ermöglicht das Festlegen eines bestimmten Stapelrahmens.

## <a name="syntax"></a>Syntax

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumente
 `index`

 Erforderlich. Wählt einen Stapelrahmen über dessen Index aus.

## <a name="example"></a>Beispiel

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)