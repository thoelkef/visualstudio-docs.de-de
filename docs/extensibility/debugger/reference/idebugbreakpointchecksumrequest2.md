---
title: "IDebugBreakpointChecksumRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBreakpointChecksumRequest2-Schnittstelle"
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt eine Anforderung Haltepunkt für eine prüfsumme Dokumente dar.  
  
## Syntax  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Wird von [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Paket die Debug\- und Module von Debuginformationen genutzt.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointChecksumRequest2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Ruft die prüfsumme für eine gegebene Haltepunkt Anforderungen der eindeutige Bezeichner des Prüfsummenalgorithmus ab, der verwendet werden soll.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Bestimmt, ob die Prüfsumme für dieses Dokument aktiviert ist.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll