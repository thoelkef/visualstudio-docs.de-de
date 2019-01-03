---
title: IDebugEngine2::RemoveSetException | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e8b4fd1d185cd5be3af3815e7c5520583231c06
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866019"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Entfernt die angegebene Ausnahme an, damit sie nicht mehr von der Debug-Engine verarbeitet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pException`  
 [in] Ein [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die die Ausnahme zu entfernenden beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Ausnahme, die entfernt werden muss zuvor festgelegt wurden durch einen früheren Aufruf von der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) Methode.  
  
 Um alle Ausnahmen, die Gruppe auf einmal entfernen, rufen die [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)