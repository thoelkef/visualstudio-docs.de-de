---
title: "IActiveScriptSiteDebug-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug-Schnittstelle"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug-Schnittstelle
Smarthosts implementieren die `IActiveScriptSiteDebug`\-Schnittstelle, um Dokumentenverwaltung auszuführen und beim Debuggen teilnehmen.  Das Objekt stellt `IActiveScriptSite` in der Regel eine Implementierung der `IActiveScriptSiteDebug`\-Schnittstelle.  Daraufhin wird, rufen Sie die `IActiveScriptSite::QueryInterface`\-Methode auf, um die `IActiveScriptSiteDebug`\-Schnittstelle zu erhalten.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IActiveScriptSiteDebug`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Wird vom Sprachmodul, um `IDebugCodeContext::GetSourceContext` zu delegieren.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Gibt die Debug\- Anwendungsobjekt zurück, das dieser Skriptsite zugeordnet ist.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Ruft den Anwendungsknoten ab, unter dem Skriptdokumente hinzugefügt werden sollen.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Ermöglicht einem Smarthost, um festzustellen, wie Laufzeitfehler behandelt.|