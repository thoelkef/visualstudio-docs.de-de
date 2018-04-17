---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a0813e077d8bdc2ba024dc932a6cb571b1b2fed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Erstellt einen ausstehenden Haltepunkt in der Debugging-Modul (DE).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pBPRequest`  
 [in] Ein [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) -Objekt, das beschreibt, die ausstehenden Haltepunkt zu erstellen.  
  
 `ppPendingBP`  
 [out] Gibt eine [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Objekt, das die ausstehenden Haltepunkt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. In der Regel gibt `E_FAIL` Wenn die `pBPRequest` Parameter entspricht einer beliebigen Sprache, die von der DE zurück, wenn unterstützt nicht die `pBPRequest` Parameter ist ungültig oder unvollständig.  
  
## <a name="remarks"></a>Hinweise  
 Ein ausstehender Haltepunkt ist im Wesentlichen eine Auflistung von alle Informationen, die zum Binden eines Haltepunkts an Code benötigt. Die von dieser Methode zurückgegebene ausstehende Haltepunkt nicht an den Code bis gebunden ist die [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) -Methode aufgerufen wird.  
  
 Für jede ausstehender Haltepunkt Ruft die Benutzersätze der Sitzungs-Manager (SDM) diese Methode in jeder angefügten Deutschland. Es liegt im Ermessen der DE, um sicherzustellen, dass der Haltepunkt für Programme, die in diesem DE ausgeführt gültig ist.  
  
 Wenn der Benutzer einen Haltepunkt in einer Zeile des Codes festgelegt, ist die DE frei, um den Haltepunkt an der nächsten Zeile im Dokument binden, die für diesen Code entspricht. Dadurch kann der Benutzer zum Festlegen eines Haltepunkts in der ersten Zeile einer Anweisung mehrere Zeilen, aber in der letzten Zeile (wobei der gesamte Code in den Debuginformationen attributiert ist) zu binden.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie diese Methode für eine einfache implementiert `CProgram` Objekt. Die DE Implementierung der `IDebugEngine2::CreatePendingBreakpoint` könnte dann alle Aufrufe an dieser Implementierung der Methode in jedem Programm weiterleiten.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)