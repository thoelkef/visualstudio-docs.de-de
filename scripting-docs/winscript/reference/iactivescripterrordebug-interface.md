---
title: "IActiveScriptErrorDebug-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug-Schnittstelle"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug-Schnittstelle
Stellt Dokumentenkontextinformationen für Kompilierungsfehler und Laufzeitausnahmen bereit.  Die `IActiveScriptError::QueryInterface`\-Methode `IActiveScriptErrorDebug` unterstützt die Schnittstelle.  
  
 Zusätzlich zu den von `IActiveScriptError` geerbten Methoden macht die `IActiveScriptErrorDebug`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Stellt den Dokumentenkontext für diesen Fehler.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Stellt den Stapelrahmen bereit, der für Laufzeitfehler wirksam ist.|