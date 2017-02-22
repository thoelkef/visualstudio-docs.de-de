---
title: "IDebugProgramNameChangedEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgramNameChangedEvent2-Schnittstelle"
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNameChangedEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Von der Debugging-Modul (DE) an gesendet der Sitzung-Manager (SDM) ändert sich der Name eines Programms.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle zum Bericht, der der Namen des Programms geändert wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface](/visual-cpp/atl/queryinterface) für den Zugriff auf die **IDebugEvent2** Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 DE erstellt und sendet diese Ereignisobjekt Änderung eines Programms zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch das SDM angegeben wird, wenn er zum gedebuggten Programm angefügt. Der benutzerdefinierten Ports Zulieferer schickt die dieses Ereignis mit der Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll