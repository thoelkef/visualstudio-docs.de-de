---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords: IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8950a69c5086616bc5f0b3177e5c6aa9aad9dfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Ruft das Ergebnis der Auswertung von Ausdrücken ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppResult`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das das Ergebnis der Auswertung des Ausdrucks darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Das zurückgegebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt enthält den Wert des ausgewerteten Ausdrucks. Beachten Sie, dass dieser Wert kann einen komplexen Wert z. B. ein Array sein, aber das Endergebnis muss eine numerische oder ein Zeichenfolgenwert, der dem Benutzer angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)