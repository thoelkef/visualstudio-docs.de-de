---
title: 'IDebugExpressionEvaluationCompleteEvent2:: GetResult | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73227762270fe4e22e6edc2643ede2d1e7a9bd70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148721"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Ergebnis der Ausdrucks Auswertung ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 vorgenommen Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das das Ergebnis der Ausdrucks Auswertung darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Das zurückgegebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt enthält den Wert des ausgewerteten Ausdrucks. Beachten Sie, dass es sich bei diesem Wert um einen komplexen Wert, z. b. ein Array, handeln kann, das Endergebnis jedoch ein numerischer Wert oder ein Zeichen folgen Wert sein muss  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
