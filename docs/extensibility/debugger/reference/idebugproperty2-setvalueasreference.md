---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7bd9e42ae6be1cbd5afe1cbe2ae1b06da7f9937f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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