---
title: "IDebugDocumentTextExternalAuthor-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor-Schnittstelle"
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor-Schnittstelle
Ermöglicht Editoren externe sicher zu bearbeiten Debuggerdokumente dateibasierte indem Benachrichtigen des Dokuments, wenn die Quelldatei geändert wird.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugDocumentTextExternalAuthor`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|Gibt den vollständigen Pfad und Dateinamen des Dokuments zurück.|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|Gibt den Namen des Dokuments ohne Pfadinformationen zurück.|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|Benachrichtigt den Host, dass die Dokumentenquelle geändert hat.|