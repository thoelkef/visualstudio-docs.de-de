---
title: "IActiveScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptError-Schnittstelle"
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError
Ein Objekt, das diese Schnittstelle implementiert, wird der [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)\-Methode übergeben, wenn das Skriptmodul einen nicht behandelten Fehler auftritt.  Der Host ruft dann Methoden für dieses Objekt an, erhält Informationen zum Fehler, der aufgetreten ist.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Ruft Informationen über einen Fehler.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Ruft den Speicherort im Quellcode ab, in dem ein Fehler aufgetreten ist.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Ruft die Zeile in der Quelldatei ab, in der ein Fehler aufgetreten ist.|  
  
## Siehe auch  
 [Active Script\-Schnittstellen](../../winscript/reference/active-script-interfaces.md)