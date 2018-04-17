---
title: UnInit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 735eb1948acfb03a6aa1a70fb27f012c41bb097d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
 [Init](init.md)