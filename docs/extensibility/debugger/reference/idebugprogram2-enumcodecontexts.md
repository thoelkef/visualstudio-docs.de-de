---
title: IDebugProgram2::EnumCodeContexts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b1bf8039d9602bee59ff31996d2a424de28ae9bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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