---
title: IDebugCodeContext2::GetDocumentContext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd0fa6dd8d587ade2ca06c3f39f65fb3a5fd295d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822188"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ruft ab, der Dokumentenkontext, der an diesen Codekontext entspricht. Den Dokumentenkontext darstellt, eine Position in der Quelldatei, die auf den Quellcode entspricht, die diese Anweisung generiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppSrcCxt`  
 [out] Gibt die [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekt, das den Codekontext entspricht.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Im Allgemeinen kann der Dokumentenkontext betrachtet werden als eine Position in einer Quelldatei während der Codekontext eine Position ein Code-Anweisung in einen Stream für die Ausführung ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)