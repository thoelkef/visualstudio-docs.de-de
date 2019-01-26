---
title: IDebugAlias2::GetAppDomainId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b70b26cbf9248f654836a2d138ad0f79b80a3b54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011745"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Ruft den Bezeichner für die Anwendungsdomäne ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pappDomainId`  
 [out] Gibt den Bezeichner der Anwendungsdomäne zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Anwendung Domäne Bezeichner ändern, wenn die Anwendung neu gestartet wird und eine neue Anwendungsdomäne erstellt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)