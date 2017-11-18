---
title: UnInit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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