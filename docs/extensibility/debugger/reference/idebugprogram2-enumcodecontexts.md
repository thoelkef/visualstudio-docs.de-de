---
title: IDebugProgram2::EnumCodeContexts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c90afe268a68d6a72e4444dd78a5748d30ddf7b6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Ruft eine Liste der Kontexte Code für eine bestimmte Position in einer Quelldatei ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDocPos`  
 [in] Ein [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) Objekt, das eine abstrakte Position in einer Quelldatei, die bekanntermaßen von der IDE darstellt.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) -Objekt, das eine Liste der Kontexte Code enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht das Debuggen Sitzung Manager (SDM) oder IDE, um eine Quelle Dateiposition an einer Position Code zuzuordnen. Mehr als einem Codekontext wird zurückgegeben, wenn die Quelle mehrere Codeblöcke (z. B. C++-Vorlagen) generiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)