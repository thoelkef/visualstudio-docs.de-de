---
title: Befehl "Symbolpfad"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3debe7c0a193cc0dc2c07875ebb32ac45a7741fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949258"
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

## <a name="remarks"></a>Hinweise
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

## <a name="see-also"></a>Siehe auch

- [Befehlsfenster](../../ide/reference/command-window.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)