---
title: IDebugProgram2::GetDebugProperty | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d19761f833472e24b07e836d08c1d9635c09b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878181"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Ruft die Anwendung die Eigenschaften ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppProperty`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das die Eigenschaften des Programms darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die von dieser Methode zurückgegebenen Eigenschaften sind spezifisch für die Anwendung. Wenn die Anwendung mehr als eine Eigenschaft zurückgeben muss die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) von dieser Methode zurückgegebene Objekt ist ein Container für zusätzliche Eigenschaften und Aufrufen der [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methode gibt ein Liste aller Eigenschaften.  
  
 Ein Programm kann verfügbar machen, beliebiger Anzahl und Art von zusätzlichen Eigenschaften, die über beschrieben werden, kann die `IDebugProperty2` Schnittstelle. Eine IDE möglicherweise die Eigenschaften der zusätzliche Anwendung über eine generische Eigenschaft-Browser-Benutzeroberfläche angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)