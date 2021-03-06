---
title: 'IDebugThread2:: getlogicalthread | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f430ea7ba69ca55bc76543d853396e22b193cf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153052"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode wird von Debug-engines nicht implementiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 in Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Objekt, das den Stapel Rahmen darstellt.  
  
 `ppLogicalThread`  
 vorgenommen Gibt eine- `IDebugLogicalThread2` Schnittstelle zurück, die den zugeordneten logischen Thread darstellt. Eine Debug-Engine-Implementierung sollte diese auf einen NULL-Wert festlegen.  
  
## <a name="return-value"></a>Rückgabewert  
 Debug-Engine-Implementierungen geben immer zurück `E_NOTIMPL` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
