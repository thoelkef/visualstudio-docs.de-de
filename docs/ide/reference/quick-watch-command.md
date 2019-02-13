---
title: Befehl "Aktuellen Wert anzeigen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e45a6c63cb1f886c1440b93d58f944458f61290
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55969866"
---
# <a name="quick-watch-command"></a>Befehl "Aktuellen Wert anzeigen"
Zeigt den ausgewählten oder angegebenen Text im Feld „Ausdruck“ des Fensters [Schnellüberwachung](../../debugger/watch-and-quickwatch-windows.md) an. Sie können dieses Dialogfeld verwenden, um den aktuellen Wert einer Variablen, eines Ausdrucks oder den Inhalt eines Registers zu berechnen, der vom Debugger erkannt wird. Darüber hinaus können Sie den Wert jeder nicht konstanten Variablen oder den Inhalt jedes Registers ändern.

## <a name="syntax"></a>Syntax

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumente
 `text`

 Dies ist optional. Der Text, der zum Dialogfeld **Schnellüberwachung** hinzugefügt werden soll.

## <a name="remarks"></a>Hinweise
 Wenn `text` ausgelassen wird, wird der aktuell ausgewählte Text oder das Wort an der Curserposition zum Überwachungsfenster hinzugefügt.

## <a name="example"></a>Beispiel

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Siehe auch

- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio (Festlegen einer Überwachung von Variablen in den Fenstern „Überwachung“ und „Schnellüberwachung“ in Visual Studio)](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)