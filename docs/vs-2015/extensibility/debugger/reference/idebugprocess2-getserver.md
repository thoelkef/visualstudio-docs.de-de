---
title: IDebugProcess2::GetServer | Microsoft-Dokumentation
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
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c23d859cd71bab09e307ea15358aa0cca9140e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729930"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Server ab, dem diesen Prozess ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetServer(   
   IDebugCoreServer2** ppServer  
);  
```  
  
```csharp  
int GetServer(   
   out IDebugCoreServer2 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppServer`  
 [out] Gibt eine [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) -Objekt, das den Server darstellt, auf dem dieser Vorgang ausgeführt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Mehr als ein Server kann auf einem einzelnen Computer ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

