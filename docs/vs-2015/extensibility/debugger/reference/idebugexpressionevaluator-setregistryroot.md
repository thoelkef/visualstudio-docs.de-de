---
title: 'Idebugexpressionevaluator:: "abtregistryroot" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e01c340b571854011966e9feeef116fab0b7d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540510"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode legt den Registrierungs Stamm fest. Wird für Paralleles Debuggen verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Der neue Registrierungs Stamm.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der angegebene Registrierungs Stamm wird in der Regel festgelegt, wenn die Ausdrucks Auswertung zuerst instanziiert wird, und verweist auf den Registrierungsschlüssel für eine bestimmte Version von Visual Studio (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ *X. y*, wobei *x. y* eine Versionsnummer ist).  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
