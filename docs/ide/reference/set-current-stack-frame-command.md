---
title: Befehl "Aktuellen Stapelrahmen festlegen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95f8c762f16eb4a784ccc2cffb5bfa27d215370e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704797"
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
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)