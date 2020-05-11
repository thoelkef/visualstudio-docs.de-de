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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 088fe9871b54e69b015ffdc9dcdaf23de3d98e0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747755"
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

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)