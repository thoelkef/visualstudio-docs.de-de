---
title: Befehl "Symbolpfad"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83acc551c778fdb245b3bacec164a7544253d55f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808690"
---
# <a name="symbol-path-command"></a>Befehl "Symbolpfad"
Legt die Liste mit Verzeichnissen fest, in denen der Debugger nach Symbolen sucht.

## <a name="syntax"></a>Syntax

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumente
`pathname`

Dies ist optional. Ein durch Semikolons getrennte Liste der Pfade, in denen der Debugger nach Symbolen sucht.

## <a name="remarks"></a>Bemerkungen
Wenn kein `pathname` angegeben wird, werden von dem Befehl die aktuellen Symbolpfade aufgelistet.

## <a name="example-1"></a>Beispiel 1
In diesem Beispiel werden der Liste mit Symbolverzeichnissen zwei Pfade hinzugefügt.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Beispiel 2
In diesem Beispiel wird eine durch Semikolons getrennte Liste der aktuellen Symbolpfade angezeigt.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Weitere Informationen

- [Befehlsfenster](../../ide/reference/command-window.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
