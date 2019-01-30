---
title: Befehl "Überwachung"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f979162dbbef7c04372d42d9ab693b013f33b8ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923334"
---
# <a name="watch-command"></a>Befehl "Überwachung"
Erstellt und öffnet eine angegebene Instanz des Fensters **Überwachen** . Sie können das Fenster **Überwachen** verwenden, um die Werte von Variablen, Ausdrücken und Registern zu berechnen, um diese Werte zu berechnen und die Ergebnisse zu speichern.

## <a name="syntax"></a>Syntax

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumente
 `index`

 Erforderlich. Die Instanznummer des Fensters „Überwachen“.

## <a name="remarks"></a>Hinweise
 Der `index` muss eine ganze Zahl sein. Gültige Werte sind 1, 2, 3 oder 4.

## <a name="example"></a>Beispiel

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Siehe auch

- [Fenster „Auto“ und „Lokal“](../../debugger/autos-and-locals-windows.md)
- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio (Festlegen einer Überwachung von Variablen in den Fenstern „Überwachung“ und „Schnellüberwachung“ in Visual Studio)](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)