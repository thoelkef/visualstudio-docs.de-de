---
title: IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03fbc1499372221a815eb639442af586f7020cf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100808"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Ruft den Dokumentenkontext, der die Position im Dokument wird beschrieben, die durch das debugpaket active vorgenommen werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDocContext`  
 [out] Gibt eine [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekt, das eine Position in einer Datei-Quelldokument darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Position kann verwendet werden, um z. B. die Einfügemarke anzuzeigen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)