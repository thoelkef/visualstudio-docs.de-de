---
title: "IDebugDefaultPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "IDebugDefaultPort2-Schnittstelle"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt mehrere Methoden für den Zugriff auf Server\- und Benachrichtigungsfunktionen eines Anschlusses bereit.  
  
## Syntax  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um den Port für den Zugriff auf Debuggen von Programmen darzustellen.  Ein benutzerdefinierter Port lieferant kann diese Schnittstelle implementieren auch beim Remotedebuggen behandelt.  
  
## Hinweise für Aufrufer  
 Ein Argument an die Methoden für das [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)\-Schnittstelle stellt diese Schnittstelle.  Das Aufrufen von [QueryInterface](/visual-cpp/atl/queryinterface) auf einer [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle kann auch Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden, die in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)definiert diese Schnittstelle implementiert, werden die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ruft den Anschluss benachrichtigungs Oberfläche von diesem Anschluss ab.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ruft die Schnittstelle zum Server, der diesen Port hostet.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bestimmt, ob dieser Anschluss auf dem lokalen Computer ausgeführt wird.|  
  
## Hinweise  
 Der Name „`IDebugDefaultPort2`“ ist ein Bit einer irrtümlichen Bezeichnung, da sie keinen Standardport darstellt.  Es könnte die Bezeichnung „IDebugPort3“.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)