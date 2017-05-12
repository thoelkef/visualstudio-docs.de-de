---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse-Schnittstelle"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
Wenn das Windows Script\-Modul die dem Skript ermöglicht hinzugefügt werden Rohtextcodeskriptlets, oder den zur Laufzeit ausgewertet werden kann, Ausdruckstext, es `IActiveScriptParse`, implementiert die Schnittstelle.  Für interpretierte Skriptsprachen, die keine unabhängige Erstellungsumgebung, wie VBScript haben, stellt dies ein alternativer Mechanismus \(außer `IPersist*`\) um Skriptcode in das Skriptmodul abzurufen, und Skriptfragmente zu verschiedenen Objektereignissen anzufügen.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialisiert das Skriptmodul.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Fügt ein Codeskriptlet dem Skript hinzu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analysiert das angegebene Codeskriptlet, fügt Deklarationen in den Namespace sowie ggf. wertet Code aus.|  
  
## Siehe auch  
 [Active Script\-Schnittstellen](../../winscript/reference/active-script-interfaces.md)