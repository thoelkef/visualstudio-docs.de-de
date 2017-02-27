---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierDescription2-Schnittstelle"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktiviert das [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, um Text innerhalb des **ÜbertragungsinformationenAn den Prozess anhängen**\-Abschnitt des Dialogfelds angezeigt.  
  
## Syntax  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von den Anschlusslieferanten implementiert.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugPortSupplierDescription2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Ruft die Beschreibung und die Eigenschaftenmetadaten für den Anschlusslieferanten ab.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll