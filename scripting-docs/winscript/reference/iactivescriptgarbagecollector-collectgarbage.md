---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645730"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Die Active Script Host ruft diese Methode zum Starten der Garbagecollection.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptgctype`  
 [in] Die [SCRIPTGCTYPE-Enumeration](../../winscript/reference/scriptgctype-enumeration.md) die angibt, ob normal oder vollständige Garbagecollection auszuführen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptGarbageCollector-Schnittstelle](../../winscript/reference/iactivescriptgarbagecollector-interface.md)