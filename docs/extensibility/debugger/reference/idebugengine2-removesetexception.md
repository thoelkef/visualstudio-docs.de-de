---
title: IDebugEngine2::RemoveSetException | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4880bfc80f27c362deb056b176492eb62ec6f975
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941546"
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