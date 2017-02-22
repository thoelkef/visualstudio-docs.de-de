---
title: "IDebugArrayObject2 | Microsoft Docs"
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
  - "IDebugArrayObject2-Schnittstelle"
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt ein verwaltetes Array\-Objekt dar und ermöglicht eine Auswertung eines Ausdrucks \(EE\), um den Basisindex \(Untergrenze\) für das Array zu bestimmen.  
  
## Syntax  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## Hinweise für Implementierer  
 Dies ist das verwaltete Debugging\-Modul \(DE\) implementiert.  
  
## Methoden  
 Zusätzlich zu den Methoden für die [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Ruft den Basis\-Indizes \(Untergrenze\) für jeden Index, der die Anzahl der Dimensionen im Array angegeben.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Bestimmt, ob das Array Basis Indizes \(untere Grenze\) definiert wurde.|  
  
## Hinweise  
 Eine Auswertung eines Ausdrucks verwendet diese Schnittstelle für verwaltete Arrays in eine Analysestruktur darstellen.  
  
## Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll