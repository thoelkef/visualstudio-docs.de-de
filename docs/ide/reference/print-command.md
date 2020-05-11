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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567839"
---
# <a name="print-command"></a>Drucken (Befehl)

Wertet einen Ausdruck aus oder zeigt angegebenen Text an.

## <a name="syntax"></a>Syntax

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumente

`text`

Erforderlich. Der auszuwertende Ausdruck oder der anzuzeigende Text

## <a name="remarks"></a>Bemerkungen

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

## <a name="see-also"></a>Weitere Informationen

- [Anweisung auswerten (Befehl)](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
