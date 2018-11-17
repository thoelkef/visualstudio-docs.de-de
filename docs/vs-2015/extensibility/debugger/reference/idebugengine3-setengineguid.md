---
title: IDebugEngine3::SetEngineGuid | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f398405a3773752d2dc0ecd11f8f0cb1b1a10aa5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743679"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode legt fest, der Debug-Engine (DE) `GUID`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetEngineGuid(  
   GUID* guidEngine  
);  
```  
  
```  
[C#]  
int SetEngineGuid(  
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidEngine`  
 [in] `GUID` des Datenbankmoduls.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

