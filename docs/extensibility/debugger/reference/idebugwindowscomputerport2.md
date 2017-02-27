---
title: "IDebugWindowsComputerPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugWindowsComputerPort2-Schnittstelle"
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Behält die Abfragen Informationen über den Zielcomputer.  
  
## Syntax  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von Objekten Port Debuggen des Managers der Sitzung implementiert.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugWindowsComputerPort2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Ruft Informationen über den Computer ab, auf dem sich der Debugger im ausgeführt.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll