---
title: "IActiveScriptDebug-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug-Schnittstelle"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug-Schnittstelle
Wird von Skriptmodule, die das Debuggen unterstützen.  In der Regel implementiert ein Objekt, das die `IActiveScriptDebug`\-Schnittstelle implementiert, auch die `IActiveScript`\-Schnittstelle.  Wenn dies der Fall ist, rufen Sie die `IActiveScript::QueryInterface`\-Methode auf, erhält die `IActiveScriptDebug`\-Schnittstelle.  
  
 Die `IActiveScriptDebug`\-Schnittstelle stellt die Mittel bereit:  
  
-   Smarthosts, um die Dokumentenverwaltung anzuwenden.  
  
-   Debuggen Manager des Prozesses, um das Debuggen mehrerer Skriptmodule zu synchronisieren.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IActiveScriptDebug`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Gibt die Textattribute für einen beliebigen Block Skripttext zurück.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Gibt die Textattribute für ein beliebiges Skriptlet zurück.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delegaten zu `IDebugDocumentContext::EnumCodeContexts`.|