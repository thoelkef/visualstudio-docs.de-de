---
title: "IDebugAlias2 | Microsoft Docs"
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
  - "IDebugAlias2-Schnittstelle"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt einen numerischen Alias für eine Variable dar und ermöglicht eine Auswertung eines Ausdrucks \(EE\), um die Anwendungsdomäne für den Alias zu erhalten.  
  
## Syntax  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle ist das verwaltete Debugging\-Modul \(DE\) implementiert.  
  
## Methoden  
 Zusätzlich zu den Methoden für die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) \-Schnittstelle, diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Ruft den Bezeichner für die Anwendungsdomäne.|  
  
## Hinweise  
 Ein Alias ist eine Dezimalzahl in Form einer Zeichenfolge gefolgt von dem \#\-Zeichen, z. B. 1001\#.  
  
## Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll