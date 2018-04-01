---
title: IDebugExpressionEvaluator::SetLocale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fe9dd81fad59c526233a56f1c5bcd1a178ad46f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Diese Methode legt die Sprache zum Erstellen von druckbaren Ergebnisse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `wLangID`  
 [in] Die Sprachen-ID.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann mehrfach aufgerufen werden, während der Auswertung eines Ausdrucks (EE) geladen wird, damit die EE Sprachen bei laufendem Betrieb wechseln sein muss. Die EE wird dieses Gebietsschema zum Zurückgeben von Fehlermeldungen und Zeichenfolgen in der entsprechenden Sprache verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)