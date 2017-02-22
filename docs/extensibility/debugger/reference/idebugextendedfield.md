---
title: "IDebugExtendedField | Microsoft Docs"
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
  - "IDebugExtendedField-Schnittstelle"
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExtendedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erweitert die Typen von Feldern, die verfügbar sind, verwalteten Code generika zu unterstützen.  
  
## Syntax  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## Methoden  
 Zusätzlich zu den Methoden der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Ruft die angegebene erweiterte Feld Testergebnisart ab.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Bestimmt, ob das Feld einen geschlossenen Typ darstellt.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll