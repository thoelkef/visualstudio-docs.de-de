---
title: 'Idebugexpressionevaluator:: setlocale | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 730a105b12016ea031bdb4753da009223a5d39f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540523"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode legt die Sprache fest, die zum Erstellen von druckbaren Ergebnissen verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Der Sprachen Bezeichner.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird möglicherweise mehrmals aufgerufen, während die Ausdrucks Auswertung (EE) geladen wird, sodass der EE in der Lage sein muss, die Sprachen im Handumdrehen zu wechseln. Der EE verwendet dieses Gebiets Schema, um Fehlermeldungen und Zeichen folgen in der entsprechenden Sprache zurückzugeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
