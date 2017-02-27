---
title: "IDebugTypeFieldBuilder2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugTypeFieldBuilder2-Schnittstelle"
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erweitert das **IDebugTypeFieldBuilder,** um in der Lage zu sein, Arraytypen zu erstellen.  
  
## Syntax  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle kann im Symbol für abgerufen werden.  
  
## Methoden  
 Zusätzlich zu den Methoden der [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)\-Schnittstelle implementiert diese Schnittstelle die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Erstellt ein Array des angegebenen Typs und Größe.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll