---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugNoSymbolsEvent2-Schnittstelle"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Signalisiert den [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger Benutzeroberfläche, um den Benutzer zu warnen, dass keine Symbole für die gestartete ausführbare Datei befinden können.  
  
## Syntax  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Wird von Debugsymbolinformationen auf Module und durch den [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger Benutzeroberfläche genutzt.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll