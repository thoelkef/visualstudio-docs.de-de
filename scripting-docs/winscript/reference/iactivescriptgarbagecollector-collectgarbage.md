---
title: 'Iactivescriptgarbagecollector:: CollectGarbage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573584"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Der aktive Skript Host ruft diese Methode auf, um Garbage Collection zu starten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptgctype`  
 in Die [scriptgctype-Enumeration](../../winscript/reference/scriptgctype-enumeration.md) , die angibt, ob normal oder vollständig Garbage Collection werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptGarbageCollector-Schnittstelle](../../winscript/reference/iactivescriptgarbagecollector-interface.md)