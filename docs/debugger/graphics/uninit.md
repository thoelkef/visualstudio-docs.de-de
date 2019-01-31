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
ms.openlocfilehash: 48c4e76105c024f9f414a884c2e3cabde716db86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019108"
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