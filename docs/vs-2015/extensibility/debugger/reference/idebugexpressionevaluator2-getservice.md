---
title: IDebugExpressionEvaluator2::GetService | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af73b23cfaf0b282403e8e6a94d6f05db419bd41
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62540341"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft ein Dienstobjekt unter Berücksichtigung den eindeutigen Bezeichner ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `uid`  
 [in] Eindeutiger Bezeichner des abzurufenden Dienstes.  
  
 `ppService`  
 [out] Gibt ein Objekt, das den Dienst darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Dies kann von einem Drittanbieter-ausdrucksauswertung zum Abrufen von Diensten aus einem anderen ausdrucksauswertung genutzt werden. Beispielsweise kann diese Methode zum Abrufen der Schnittstelle für den schnellansichtsdienst aus der Standard-ausdrucksauswertung verwendet werden. Drittanbieter--ausdruckauswertung ist es unwahrscheinlich, dass diese Schnittstelle implementieren müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
