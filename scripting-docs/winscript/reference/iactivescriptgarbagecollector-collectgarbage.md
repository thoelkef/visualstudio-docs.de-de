---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft-Dokumentation
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
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144666"
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