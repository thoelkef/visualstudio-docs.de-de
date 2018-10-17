---
title: IDebugExpressionEvaluator2::GetService | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c93f7585c03b4df1e7c260b9b8e41436dcd86ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201668"
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

