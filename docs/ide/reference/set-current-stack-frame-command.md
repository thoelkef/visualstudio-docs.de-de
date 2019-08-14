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
ms.openlocfilehash: 24880f997d604d3db11ae19a6220c2789da7648f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926075"
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