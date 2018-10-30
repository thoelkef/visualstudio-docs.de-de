---
title: IDebugProgram2::EnumCodeContexts | Microsoft-Dokumentation
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
ms.openlocfilehash: ddd3f6f3fe06b0a02a1df992561428aa04895748
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902515"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Ruft eine Liste der Codekontexte für eine bestimmte Position in einer Quelldatei.  
  
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
 [in] Ein [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) Objekt, das eine abstrakte Position in einer Quelldatei bekannt, dass die IDE darstellt.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) -Objekt, das eine Liste der Codekontexte enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode können die Sitzung-Debug-Manager (SDM) oder eine IDE, um eine Quelle Dateiposition an einer Position Code zuzuordnen. Mehr als einem Codekontext wird zurückgegeben, wenn die Quelle mehrere Blöcke von Code (z. B. C++-Vorlagen) generiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)