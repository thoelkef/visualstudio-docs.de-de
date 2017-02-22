---
title: "IDebugProgramHost2 | Microsoft Docs"
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
  - "IDebugProgramHost2"
helpviewer_keywords: 
  - "IDebugProgramHost2-Schnittstelle"
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle bereitstellt \(process\) des Hosts über ein Programm.  
  
## Syntax  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul implementiert diese Schnittstelle für dasselbe Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle, um Informationen über den Hostprozess bereitzustellen.  Hierbei handelt es sich um eine optionale Schnittstelle.  
  
## Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugProgram2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProgramHost2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ruft den Titel des Anzeigenamens, oder der Dateiname des Prozesses Hosten des Programms ab.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ruft die Prozess\-ID des Prozesses Hosten des Programms ab.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ruft den Namen des Computers ab, auf dem der Hostprozess dieses Programms an ausführt.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)