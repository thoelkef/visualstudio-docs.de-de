---
title: "IDebugDocumentHost-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost-Schnittstelle"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost-Schnittstelle
Setzt hostspezifische Funktionen, wie Syntaxfarbe, dem Debugger aus.  Die `IDebugDocumentHelper::SetDebugDocumentHost`\-Methode nimmt diese Schnittstelle als Argument.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugDocumentHost`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Gibt einen Bereich von Zeichen, die hinzugefügt wurden, indem `IDebugDocumentHelper::AddDeferredText` verwendete, im ursprünglichen Hostdokument zurück.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Gibt die Textattribute für einen Block Dokumenttext zurück.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Benachrichtigt den Host, dass ein Kontext des neuen Dokuments erstellt und dem Host ermöglicht wird, um optional ein Objekt zurückzugeben, das den neuen Kontext steuert.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Gibt den vollständigen Pfad \(einschließlich des Dateinamens\) der Quelldatei des Dokuments zurück.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Gibt den Namen des Dokuments, ohne Pfadinformationen zurück.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Benachrichtigt den Host, dass die Quelldatei des Dokuments gespeichert wurde und dass sein Inhalt aktualisiert werden soll.|