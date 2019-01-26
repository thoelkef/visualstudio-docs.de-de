---
title: IDebugEvent2::GetAttributes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dffc2bbd858fa7c8bcc31825de79dcdc4b9a60ac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040189"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Ruft die Attribute für dieses Ereignis Debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwAttrib`  
 [out] Eine Kombination von Flags aus der [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle ist für alle Ereignisse. Diese Methode beschreibt den Typ des Ereignisses; Beispielsweise ist das Ereignis, synchron oder asynchron, und ist es eine Beenden-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)