---
title: IDebugExpressionEvaluator2::SetCallback | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9e10980c1ed075b9ce1f06b6bb945cdf42263546
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910164"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Ermöglicht die ausdrucksauswertung (EE) an die Rückrufschnittstelle, die die Debugger-Engine (DE) verwenden, lesen Sie die Metric-Einstellung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCallback`  
 [in] Die Schnittstelle, die für den Rückruf Einstellungen verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode stellt eine Schnittstelle für die Sitzung-Debug-Manager, mit denen eine ausdrucksauswertung Metric-Einstellung zu lesen. Es eignet sich für das Remotedebuggen zum Lesen von Metriken auf die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Computer.  
  
## <a name="example"></a>Beispiel  
 In den folgenden Beispielen wird gezeigt, wie diese Methode zum Implementieren einer **CEE** -Objekt, das macht die [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) Schnittstelle.  
  
```cpp  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)