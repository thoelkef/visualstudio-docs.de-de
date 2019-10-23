---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae87afb11be71af8f0582a0b2899d67ba970186e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747820"
---
# <a name="print-command"></a>Befehl „Drucken“

Wertet einen Ausdruck aus oder zeigt angegebenen Text an.

## <a name="syntax"></a>Syntax

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumente

`text`

Erforderlich. Der auszuwertende Ausdruck oder der anzuzeigende Text

## <a name="remarks"></a>Anmerkungen

Sie können ein Fragezeichen (?) als Alias für diesen Befehl verwenden. Daher wird mit dem Befehl

```cmd
>Debug.Print expA
```

kann beispielsweise auch folgendermaßen geschrieben werden:

```cmd
? expA
```

Beide Versionen dieses Befehls geben den aktuellen Wert des Ausdrucks `expA` zurück.

## <a name="example"></a>Beispiel

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Anweisung auswerten"](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)