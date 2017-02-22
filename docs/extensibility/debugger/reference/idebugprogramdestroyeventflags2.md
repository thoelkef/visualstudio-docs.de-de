---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
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
  - "IDebugProgramDestroyEventFlags2-Schnittstelle"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktiviert eine Debug\- Modul, das Standardverhalten des [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu überschreiben, wenn Sie eine Debugsitzung beenden.  
  
## Syntax  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von Debugsymbolinformationen auf Module implementiert.  Es ist für Hosts hilfreich, die möglicherweise mehrere Programme über die Lebensdauer eines Prozesses erstellen und zerstörten.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugProgramDestroyEventFlags2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Ruft das Programm zerstören Flags ab.|  
  
## Hinweise  
 Das Standardverhalten des [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche ist, auf Programme im Entwurfsmodus zu wechseln, nachdem alle eines Programms zerstört Ereignis gesendet hat.  Diese Schnittstelle ermöglicht eine Debug\- Modul, um dieses Verhalten zu ändern.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll