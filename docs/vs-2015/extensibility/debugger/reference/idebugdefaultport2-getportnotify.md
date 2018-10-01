---
title: IDebugDefaultPort2::GetPortNotify | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a0cd508f0eab1d4ffc0feea32de128c411bef6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514562"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDefaultPort2::GetPortNotify](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdefaultport2-getportnotify).  
  
Diese Methode ruft eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Schnittstelle für diesen Port.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppPortNotify`  
 [out] Ein [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel die `QueryInterface` Methode wird aufgerufen, die Objekt-Implementierung der [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle zum Abrufen einer [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Schnittstelle. Es gibt jedoch Situationen, in denen die gewünschte Schnittstelle auf einem anderen Objekt implementiert wird. Diese Methode blendet diese Umstände und gibt die `IDebugPortNotify2` Schnittstelle aus dem am besten geeigneten-Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)

