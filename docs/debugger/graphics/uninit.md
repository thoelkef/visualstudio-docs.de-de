---
title: UnInit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8165b2e1993a6ea52127536a058f662e1a3d92cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848719"
---
# <a name="uninit"></a>UnInit
Schließt die Grafikprotokolldatei ab, schließt sie und gibt Ressourcen frei, die verwendet wurden, während die App aktiv Grafikinformationen aufzeichnete.

## <a name="syntax"></a>Syntax

```C++
void UnInit();
```

## <a name="remarks"></a>Hinweise
 `UnInit` wird automatisch aufgerufen, wenn eine Instanz der `VsgDbg`-Klasse zerstört wird. Wenn die `VsgDbg`-Instanz nicht aktiv Grafikinformationen aufzeichnete, hat dies keine Auswirkungen.

 Nachdem `UnInit` auf einer Instanz der `VsgDbg`-Klasse aufgerufen wurde, kann eine neue Grafikprotokolldatei erstellt werden, indem `Init` aufgerufen wird. Sie kann abgeschlossen werden, indem `UnInit` aufgerufen wird. Sie können dies so oft wiederholen, wie Sie möchten, um dieselbe `VsgDbg`-Instanz zum Erstellen mehrerer unabhängiger Grafikprotokolldateien zu verwenden.

## <a name="see-also"></a>Siehe auch
- [Init](init.md)