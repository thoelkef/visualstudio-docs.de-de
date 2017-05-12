---
title: "IDebugDocumentHost::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetFileName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetFileName"
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetFileName
Gibt den Namen des Dokuments ohne Pfadinformationen zurück.  
  
## Syntax  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### Parameter  
 `pbstrShortName`  
 \[out\] Eine Zeichenfolge, die den kurzen Namen des Dokuments enthält.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den kurzen Namen des Dokuments ohne Pfadinformationen zurück.  Der kurze wird in der Regel in Situationen wie dem Dialogfeld **Speichern unter...** verwendet.  
  
## Siehe auch  
 [IDebugDocumentHost\-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)