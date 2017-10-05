---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 11a0f157ff10fb7f22d7571b22ab0263c430e5dd
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
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
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel wird die `QueryInterface` Methode wird aufgerufen, auf das Objekt, durch die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle zum Abrufen einer [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Schnittstelle. Es gibt jedoch Situationen, in denen die gewünschte Schnittstelle auf einem anderen Objekt implementiert wird. Diese Methode blendet diese Umstände und gibt die `IDebugPortNotify2` Schnittstelle aus dem am besten geeigneten-Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
