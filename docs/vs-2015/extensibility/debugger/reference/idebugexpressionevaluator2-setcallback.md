---
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d6f715bb33afe051cdccffbf3219e062b606f57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179925"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ermöglicht es der Ausdrucks Auswertung (EE), die Rückruf Schnittstelle anzugeben, die die Debugger-Engine (de) zum Lesen von Metrikeinstellungen verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Schnittstelle, die für den Einstellungs Rückruf verwendet werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode stellt eine Schnittstelle zum sitzungsdebug-Manager bereit, der von einer Ausdrucks Auswertung zum Lesen von Metrikeinstellungen verwendet werden kann. Es ist beim Remote Debuggen hilfreich, um Metriken auf dem Computer zu lesen [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .  
  
## <a name="example"></a>Beispiel  
 In den folgenden Beispielen wird gezeigt, wie Sie diese Methode für ein **CEE** -Objekt implementieren, das die [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) -Schnittstelle verfügbar macht.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
