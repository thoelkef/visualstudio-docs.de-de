---
title: IDebugCanStopEvent2::GetDocumentContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e2e2f9c96780c5b409b8cd145ea554c10e54e96
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960372"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Ruft ab, der Dokumentenkontext, der den Speicherort der dieses Ereignis beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDocCxt`  
 [out] Gibt die [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle, die eine Position in einem Quelldokument-Datei entsprechend auf den aktuellen codespeicherort darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Dokumentenkontext kann in der Regel als eine Position in einer Quelldatei betrachtet werden.  
  
 Rufen Sie den Codekontext, der auf Code-Anweisungen ausgerichtet ist, rufen Sie die [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)