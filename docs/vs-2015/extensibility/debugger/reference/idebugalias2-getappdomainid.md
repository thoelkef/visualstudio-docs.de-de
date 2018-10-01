---
title: IDebugAlias2::GetAppDomainId | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8a2c766a1ec6fce1856312756adad3c5f234866
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508968"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugAlias2::GetAppDomainId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias2-getappdomainid).  
  
Ruft den Bezeichner für die Anwendungsdomäne ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

