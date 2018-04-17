---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f8d871e6193835b51336a48355fde78fe95e103
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Legt den Wert dieser Eigenschaft auf den Wert des angegebenen Verweises fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rgpArgs`  
 [in] Ein Array von Argumenten, die an den Eigenschaftensetter verwalteten Code übergeben. Wenn der Setter für eine Eigenschaft keine Argumente akzeptiert, oder wenn diese [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt verweist nicht auf solche ein Eigenschaftensetter `rgpArgs` sollte ein null-Wert sein. Dieser Parameter ist in der Regel einen null-Wert.  
  
 `dwArgCount`  
 [in] Die Anzahl der Argumente in der `rgpArgs` Array.  
  
 `pValue`  
 [in] Ein Verweis in Form einer [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt, auf den Wert für diese Eigenschaft festgelegt.  
  
 `dwTimeout`  
 [in] Wie lange zu treffen, um den Wert in Millisekunden festgelegt. Ein häufig angegebener Wert ist `INFINITE`. Dies wirkt sich auf die Länge der Zeit, die alle möglichen Auswertung.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls einen Fehler code wird zurückgegeben, in der Regel eine der folgenden:  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Festlegen des Werts aus einem Verweis wird nicht unterstützt.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Der Wert kann nicht festgelegt werden, wie diese Eigenschaft auf eine Methode verweist.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Der Wert ist schreibgeschützt und kann nicht festgelegt werden.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)