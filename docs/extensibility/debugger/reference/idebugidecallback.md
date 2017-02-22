---
title: "IDebugIDECallback | Microsoft Docs"
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
  - "IDebugIDECallback-Schnittstelle"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ermöglicht eine Auswertung eines Ausdrucks \(EE\) eine Meldung im Ausgabefenster des Debuggers angezeigt.  
  
## Syntax  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## Hinweise für Implementierer  
 Dieser Rückruf wird durch das verwaltete Debugging\-Modul implementiert.  
  
## Hinweise für Aufrufer  
 Er kann von der ausdrucksauswertung zum Senden von Ausgabe an den Debugger\-Ausgabefenster genutzt werden.  
  
## Methoden  
 Diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Sendet die angegebene Meldungszeichenfolge Ausgabefenster des Debuggers.|  
  
## Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll