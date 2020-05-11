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
ms.openlocfilehash: ed8ec8e7f990a4a2c5d943a15a105faa5ab23572
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589382"
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

## <a name="example"></a>Beispiel
In diesem Beispiel werden der Liste mit Symbolverzeichnissen zwei Pfade hinzugefügt.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Beispiel
In diesem Beispiel wird eine durch Semikolons getrennte Liste der aktuellen Symbolpfade angezeigt.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Weitere Informationen

- [Befehlsfenster](../../ide/reference/command-window.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
