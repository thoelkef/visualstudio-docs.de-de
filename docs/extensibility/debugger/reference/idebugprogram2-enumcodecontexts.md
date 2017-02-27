---
title: "IDebugProgram2::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste der Code für kontexte einer angegebenen Position in einer Quelldatei ab.  
  
## Syntax  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### Parameter  
 `pDocPos`  
 \[in\]  Ein [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)\-Objekt, das eine abstrakte Position in einer Quelldatei wird die IDE darstellt.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)\-Objekt zurück, das eine Liste der Codekontexte enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ermöglicht der Sitzung Debuggen von Manager \(SDM\) oder zuzuordnenden IDE eine Position in einer Quelldatei Position des Codes.  Mehrere Code Elementkontext wird zurückgegeben, wenn die Datenquelle mehrere Codeblöcke generiert \(beispielsweise C\+\+\-Vorlagen\).  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)