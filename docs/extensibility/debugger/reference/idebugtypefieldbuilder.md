---
title: "IDebugTypeFieldBuilder | Microsoft Docs"
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
  - "IDebugTypeFieldBuilder-Schnittstelle"
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bietet die Möglichkeit, ein Feld zu erstellen, das einen Typ darstellt.  
  
## Syntax  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird im Symbol für erhalten.  
  
## Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Erstellt ein Objekt, das einen Typ darstellt.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Stellt einen Zeiger auf den angegebenen Typ.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll