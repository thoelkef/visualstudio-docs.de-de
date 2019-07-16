---
title: UnInit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197936"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Schließt die Grafikprotokolldatei ab, schließt sie und gibt Ressourcen frei, die verwendet wurden, während die App aktiv Grafikinformationen aufzeichnete.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Hinweise  
 `UnInit` wird automatisch aufgerufen, wenn eine Instanz der `VsgDbg`-Klasse zerstört wird. Wenn die `VsgDbg`-Instanz nicht aktiv Grafikinformationen aufzeichnete, hat dies keine Auswirkungen.  
  
 Nachdem `UnInit` auf einer Instanz der `VsgDbg`-Klasse aufgerufen wurde, kann eine neue Grafikprotokolldatei erstellt werden, indem `Init` aufgerufen wird. Sie kann abgeschlossen werden, indem `UnInit` aufgerufen wird. Sie können dies so oft wiederholen, wie Sie möchten, um dieselbe `VsgDbg`-Instanz zum Erstellen mehrerer unabhängiger Grafikprotokolldateien zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Init](../debugger/init.md)
