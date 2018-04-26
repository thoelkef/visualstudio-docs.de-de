---
title: Befehl "Wurzel setzen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f23e2492a183dcae2e2b3cb87e39b08f66a7c2ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="set-radix-command"></a>Befehl "Wurzel setzen"
Legt die zum Anzeigen von ganzzahligen Werten verwendete numerische Basis fest bzw. gibt sie zurück.

## <a name="syntax"></a>Syntax

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumente
 `10` oder `16` oder `hex` oder `dec`

 Dies ist optional. Legt „dezimal“ (10 bzw. dec) oder „hexadezimal“ (16 bzw. hex) als Format fest. Wird ein Argument weggelassen, wird der aktuelle Wert der Wurzel zurückgegeben.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Umgebung zum Anzeigen ganzzahliger Werte im Hexadezimalformat konfiguriert.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)