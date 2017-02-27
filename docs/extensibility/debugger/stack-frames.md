---
title: "Stapelrahmen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen von Stapelrahmen"
  - "Debuggen [Debugging-SDK] Stapelrahmen"
  - "Stapelrahmen"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Stapelrahmen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger einen **Stapelrahmen**:  
  
-   Ist eine Abstraktion eines Stapels, der den Ausführungskontext eines Threads bereitstellt.  Ein Thread wird immer innerhalb einer Funktion aus.  Ein Stapelrahmen enthält die lokalen Variablen und Argumente der Funktion.  Um mit Visual Studio debuggen, müssen die Sprache bzw. Umgebung, die gedebuggt wird, Stapelrahmen unterstützen.  
  
-   Kann sich ermitteln und beschreiben und kann den zugeordneten Thread zurückgeben.  Ein Stapelrahmen des Codes kann der aktuelle Anweisungszeiger darstellt, sowie die zugehörigen Dokumentations\- und Ausdrucksauswertungs auch kontexte zurückgeben.  
  
-   Verfügt über Eigenschaften, die den Namen, den Typ und den Wert einer lokalen Variablen und Argumente beschrieben und die in verschiedenen Fenstern Debuggen IDE erscheinen.  
  
-   Wird von einer Schnittstelle dargestellt [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) erstellt, in der Regel durch eine Debug\- Modul \(DE\) oder virtuellen Computer als Folge der Ausführung eines Threads.  
  
## Siehe auch  
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)