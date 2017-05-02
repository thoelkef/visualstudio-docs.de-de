---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure-Schnittstelle"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
Wenn das Windows Script\-Modul den Quellcodetext die zulässt dem Skript hinzugefügt werden, Prozeduren, es `IActiveScriptParseProcedure`, implementiert die Schnittstelle.  Für interpretierte Skriptsprachen, die keine unabhängige Erstellungsumgebung, wie VBScript haben, stellt dies ein alternativer Mechanismus \(außer `IActiveScriptParse` oder `IPersist`\*\) um Skriptprozeduren dem Namespace hinzuzufügen.  
  
## Methoden in Vtable\-Reihenfolge  
  
|||  
|-|-|  
|Methode|Description|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analysiert die angegebene Kennzahlprozedur und fügt die Prozedur dem Namespace hinzu.|  
  
## Siehe auch  
 [Active Script\-Schnittstellen](../../winscript/reference/active-script-interfaces.md)