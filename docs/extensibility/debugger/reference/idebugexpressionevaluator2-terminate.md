---
title: IDebugExpressionEvaluator2::Terminate | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Terminate
- IDebugExpressionEvaluator2::Terminate
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 692165f11b9a43f62fc9d2d84faaba3c83fb5346
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902564"
---
# <a name="idebugexpressionevaluator2terminate"></a>IDebugExpressionEvaluator2::Terminate
Beendet und die ausdrucksauswertung bereinigt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Terminate (  
    void  
);  
```  
  
```csharp  
int Terminate ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Weist die ausdrucksauswertung Wenn es bereinigt wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **ExpressionEvaluatorPackage** -Objekt, das macht die [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) Schnittstelle.  
  
```cpp  
STDMETHODIMP ExpressionEvaluatorPackage::Terminate(void)  
{  
    // scan the namespaces contained and delete  
    EEExtensionMethodCache **ppChild = NULL;  
    m_HashExtensionMethodCache.ResetHashIterator();  
    while (ppChild = m_HashExtensionMethodCache.IterateHash())  
    {  
        delete *ppChild;  
    }  
    return VBEEImplicitVariables::Terminate();  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)