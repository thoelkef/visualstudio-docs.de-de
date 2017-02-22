---
title: "IDebugExpressionEvaluator2::SetCallback | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::SetCallback"
  - "SetCallback"
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator2::SetCallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktiviert die Ausdrucksauswertung \(EE\), um die Rückrufschnittstelle an, die der Debugger DE \(Modul\) verwendet werden, um Einstellungen metrischen zu lesen.  
  
## Syntax  
  
```cpp#  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```c#  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### Parameter  
 `pCallback`  
 \[in\]  Für den Rückruf Einstellungen zu verwendende \- Schnittstelle.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode stellt eine Schnittstelle zum Debuggen von Manager der Sitzung bereit, den der Ausdrucksauswertung verwendet werden kann, um metrische Einstellungen zu lesen.  Es empfiehlt sich, Metriken für das Remotedebuggen im [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Computer zu lesen.  
  
## Beispiel  
 In den folgenden Beispielen wird gezeigt, wie mit dieser Methode für ein **CEE**\-Objekt implementiert, das die [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
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
  
## Siehe auch  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)