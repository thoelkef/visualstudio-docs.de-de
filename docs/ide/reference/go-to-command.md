---
title: Befehl "Gehe zu"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fad99d77c7dc086e3e83f25b9ffea08fe60d914b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012455"
---
# <a name="go-to-command"></a>Befehl "Gehe zu"
Bewegt den Cursor in die angegebene Zeile.

## <a name="syntax"></a>Syntax

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumente
 `linenumber`

 Dies ist optional. Eine ganze Zahl, die die Zeilennummer, zu der Sie springen wollen, angibt.

## <a name="remarks"></a>Hinweise
 Die Zeilennummerierung beginnt bei eins. Wenn der Wert von `linenumber` kleiner als eins ist, wird die erste Zeile angezeigt. Wenn der Wert von `linenumber` größer als die Nummer der letzten Zeile ist, wird die letzte Zeile angezeigt.

 Wenn für `linenumber` kein Wert angegeben wird, wird das **Gehe zu Zeile**-Dialogfeld angezeigt.

 Der Alias dieses Befehls lautet „GoToLn“.

## <a name="example"></a>Beispiel

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)