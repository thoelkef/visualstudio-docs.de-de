---
title: Befehl "Gehe zu"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569204"
---
# <a name="go-to-command"></a>Befehl "Gehe zu"
Bewegt den Cursor in die angegebene Zeile.

## <a name="syntax"></a>Syntax

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumente
`linenumber`\
Dies ist optional. Eine ganze Zahl, die die Zeilennummer, zu der Sie springen wollen, angibt.

## <a name="remarks"></a>Bemerkungen
Die Zeilennummerierung beginnt bei eins. Wenn der Wert von `linenumber` kleiner als eins ist, wird die erste Zeile angezeigt. Wenn der Wert von `linenumber` größer als die Nummer der letzten Zeile ist, wird die letzte Zeile angezeigt.

Wenn für `linenumber` kein Wert angegeben wird, wird das **Gehe zu Zeile**-Dialogfeld angezeigt.

Der Alias dieses Befehls lautet „GoToLn“.

## <a name="example"></a>Beispiel

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
