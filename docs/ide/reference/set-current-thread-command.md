---
title: Befehl "Aktuellen Thread festlegen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcfbceba1cc9d0b24c135a8ce25fbd2f3d367f55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924135"
---
# <a name="set-current-thread-command"></a>Befehl "Aktuellen Thread festlegen"
Legt den angegebenen Thread als aktuellen Thread fest.

## <a name="syntax"></a>Syntax

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argumente
 `index`

 Erforderlich. Wählt einen Thread nach seinem Index aus.

## <a name="example"></a>Beispiel

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)