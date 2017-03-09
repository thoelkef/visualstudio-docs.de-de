---
title: "Anzeigen von benutzerdefinierten Datentypen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat (Datei)"
  - "Benutzerdefinierte Datentypen"
  - "Datentypen [C#], Benutzerdefiniert"
  - "Debugger, Erweitern von Datentypen"
  - "Verwalteter Code, Benutzerdefinierte Datentypen"
  - "mcee_cs.dat (Datei)"
  - "mcee_mc.dat (Datei)"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anzeigen von benutzerdefinierten Datentypen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.  
  
## Attribute  
 In C\# und Visual Basic können Sie Erweiterungen für benutzerdefinierte Daten mit <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerBrowsableAttribute> hinzufügen.  
  
 In [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]\-Code bietet Visual Basic keine Unterstützung des DebuggerBrowsable\-Attributs.  Diese Einschränkung wurde in aktuelleren Versionen von .NET Framework entfernt.  
  
## Schnellansichten  
 Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md).  
  
## Systemeigener Code  
 Für systemeigenen Code können Sie der Datei autoexp.dat benutzerdefinierte Datentyperweiterungen hinzufügen. Diese Datei befindet sich im Verzeichnis Programme\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger.  Anweisungen zum Schreiben von Regeln für die Datei `autoexp` befinden sich in der Datei selbst.  
  
> [!CAUTION]
>  Die Struktur dieser Datei und die Syntax der autoexp\-Regeln können in den verschiedenen Versionen von Visual Studio unterschiedlich sein.  
  
 Auch die Ansichten von systemeigenen Typen können angepasst werden, und zwar durch das Schreiben eines Expression Evaluator\-Add\-Ins.  Weitere Informationen finden Sie unter [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/de-de/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## Siehe auch  
 [Verwenden des DebuggerTypeProxy\-Attributs](../debugger/using-debuggertypeproxy-attribute.md)   
 [Verwenden des DebuggerDisplay\-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)