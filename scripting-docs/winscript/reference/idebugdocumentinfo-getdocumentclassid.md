---
title: "IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetDocumentClassId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetDocumentClassId"
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetDocumentClassId
Gibt `CLSID` zurück, das den Dokumenttyp identifiziert.  
  
## Syntax  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### Parameter  
 `pclsidDocument`  
 \[out\] A `CLSID`, das den Dokumenttyp identifiziert.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode kann der Debugger IDE zu benutzerdefinierten Viewern des Hosts dieses Dokument zu.  
  
 Wenn das Dokument nicht sichtbare Daten ist, ist der Rückgabewert von `pclsidDocument``CLSID_NULL`.  
  
## Siehe auch  
 [IDebugDocumentInfo\-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)