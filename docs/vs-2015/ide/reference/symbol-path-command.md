---
title: Befehl „Symbolpfad“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651005"
---
# <a name="symbol-path-command"></a>Befehl "Symbolpfad"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Liste mit Verzeichnissen fest, in denen der Debugger nach Symbolen sucht.

## <a name="syntax"></a>Syntax

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argumente
 `pathname` ist optional. Ein durch Semikolons getrennte Liste der Pfade, in denen der Debugger nach Symbolen sucht.

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
 [Befehlsfenster](../../ide/reference/command-window.md) ( [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) )
