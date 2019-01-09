---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft-Dokumentation
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
ms.openlocfilehash: 478a7a39c69e0c2106e3c6cc308f44f8f7aa3201
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097122"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Die Active Script-Host ruft diese Methode, um die Garbagecollection gestartet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parameter  
 `scriptgctype`  
 [in] Die [SCRIPTGCTYPE-Enumeration](../../winscript/reference/scriptgctype-enumeration.md) , der angibt, ob mit normaler oder vollständige Garbagecollection auszuführen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptGarbageCollector-Schnittstelle](../../winscript/reference/iactivescriptgarbagecollector-interface.md)