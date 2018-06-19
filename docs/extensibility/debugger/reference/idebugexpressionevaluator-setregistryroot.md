---
title: IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70b1730fc44deeb7e32433480f02f750c9bec193
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110197"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Diese Methode legt den Registrierungsstamm fest. Für das Debuggen von Seite-an-Seite verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ustrRegistryRoot`  
 [in] Die neue Registrierungsstamm.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der angegebene Registrierungsstamm wird in der Regel festgelegt werden, wenn die ausdrucksauswertung zuerst instanziiert und verweist auf den Registrierungsschlüssel für eine bestimmte Version von Visual Studio (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y* , wobei *X.Y* ist eine Versionsnummer).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)