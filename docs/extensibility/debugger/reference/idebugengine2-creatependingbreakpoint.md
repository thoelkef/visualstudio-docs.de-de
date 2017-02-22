---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen anstehenden Haltepunkt im Modul \(Debuggen\). DE  
  
## Syntax  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### Parameter  
 `pBPRequest`  
 \[in\]  Ein [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)\-Objekt, das den anstehenden Haltepunkt beschreibt, die erstellt werden soll.  
  
 `ppPendingBP`  
 \[out\]  Gibt ein [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)\-Objekt zurück, das den anstehenden Haltepunkt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt üblicherweise `E_FAIL` zurück, wenn der `pBPRequest`\-Parameter keine Sprache entspricht, die durch DE von unterstützt wird, wenn der `pBPRequest`\-Parameter ungültig oder unvollständig ist.  
  
## Hinweise  
 Ein anstehender Haltepunkt ist im Grunde eine Auflistung aller Informationen, die benötigt werden, um einen Haltepunkt in den Code zu binden.  Der ausstehende Haltepunkt, der aus dieser Methode zurückgegeben werden, werden nicht in den Code gebunden, bis die [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)\-Methode aufgerufen wurde.  
  
 Für jeden anstehenden Haltepunkt ruft die Benutzer der Debug\- Manager, legt der Sitzung \(SDM\) diese Methode in jedem angefügten DE an.  Er ist so viele DE sicherzustellen, dass der Haltepunkt für Programme gültig ist, die in diesem DE ausgeführt werden.  
  
 Wenn die Benutzer legt einen Haltepunkt auf eine Codezeile, DE entscheiden, ob der Haltepunkt an der nächsten Zeile im Dokument zu binden, das für diesen Code entspricht.  Auf diese Weise ist es möglich, dass der Benutzer einen Haltepunkt in der ersten Zeile einer mehrzeiligen Anweisung ändert, wird aber in der letzten Zeile \(wobei der gesamte Code in den Debuginformationen attributiert ist.\)  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CProgram`\-Objekt implementiert.  Die DEs Implementierung `IDebugEngine2::CreatePendingBreakpoint` konnte alle Aufrufe dieser Implementierung der Methode in jedem Programm weiterleiten.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)