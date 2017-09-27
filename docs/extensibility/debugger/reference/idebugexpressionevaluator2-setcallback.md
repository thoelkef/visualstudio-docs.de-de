---
title: IDebugExpressionEvaluator2::SetCallback | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e5b9964dee0580fe0fbab6d817c4dc2abf56dad4
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Ermöglicht die ausdrucksauswertung (EE) an die Rückrufschnittstelle, mit der der Debugger-Modul (DE) metrikeinstellungen zu lesen.  
  
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
 [in] Die Schnittstelle für den Rückruf Einstellungen verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode stellt eine Schnittstelle zu dem Sitzung Debug-Manager, mit denen eine ausdrucksauswertung metrikeinstellungen zu lesen. Es eignet sich für das Remotedebuggen zum Lesen von Metriken auf der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Computer.  
  
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
