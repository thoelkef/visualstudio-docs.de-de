---
title: "IDebugFunctionObject2 | Microsoft Docs"
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
  - "IDebugFunctionObject2-Schnittstelle"
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt eine Funktion dar und verbessert die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.  
  
## Syntax  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Eine Auswertung eines Ausdrucks \(EE\) implementiert diese Schnittstelle, um eine Funktion dar.  
  
## Hinweise für Aufrufer  
 Methoden dieser Schnittstelle verzögern der **IDebugFunctionObject** auf folgende Weise:  
  
-   Die **IDebugEvaluate** Methode nimmt Flags.  
  
-   Die **CreateObject** Methode nimmt Flags und ein Timeout.  
  
-   Die **CreateStringObjectWithLength** Methode nimmt eine Länge.  
  
## Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Erstellt ein Objekt, das einen bestimmte Auswertung Flageinstellungen und einen Timeoutwert Konstruktor verwendet.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Erstellt ein String\-Objekt, das die angegebene Länge aufweist.|  
|[Bewerten](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Ruft die Funktion und der resultierende Wert als Objekt zurückgegeben.|  
  
## Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll