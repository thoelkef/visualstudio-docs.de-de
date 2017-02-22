---
title: "Codekontext | Microsoft Docs"
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
  - "Debuggen [Debugging-SDK] Kontexten"
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Codekontext
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In debuggendem**Kontext des Codes**ein, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :  
  
-   Stellt eine Abstraktion einer Position im Code bereit, wie bekannte das Debugmodul \(DE\).  Für die meisten von heute architekturen können Code in einem Kontext für eine Adresse Anweisungsstream des Programms beibehalten werden.  Für nicht traditionele Sprachen, in denen Code möglicherweise nicht von Anweisungen dargestellte Code wird ein Kontext möglicherweise auf eine andere weise dargestellt.  
  
-   Beschreibt die aktuelle Position im datenstrom Ausführen des Programms, das gedebuggt wird.  
  
-   Existiert nur, wenn ein Programm bei einem Haltepunkt angehalten wurde.  
  
-   Verfügt über einen zugeordneten Dokumentenkontext.  
  
-   Wird von einer [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md)\-Schnittstelle implementiert.  
  
## Siehe auch  
 [Dokumentenkontext](../../extensibility/debugger/document-context.md)   
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)