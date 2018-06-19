---
title: IDebugThread2::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98ef4ff5a2e1896bccaab82b32c1244da9f1ca2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120048"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Ruft den Namen eines Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 [out] Gibt den Namen des Threads zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der abgerufene Name ist immer einen Namen, der angezeigt werden können, und dieser Name wird den Thread beschrieben. Threadname möglicherweise von einer Laufzeit-Architektur abgeleitet werden, dass benannter Threads unterstützt, oder es ist ein Name, der von der Debugging-Modul abgeleitet. Alternativ kann der Name des Threads festgelegt werden, durch einen Aufruf der [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)