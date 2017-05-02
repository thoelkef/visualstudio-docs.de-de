---
title: "IDebugDocumentInfo::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetName"
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetName
Gibt den angegebenen Dokumentnamen zurück.  
  
## Syntax  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### Parameter  
 `dnt`  
 \[in\] Der Typ des Dokumentnamens zurückgegeben.  
  
 `pbstrName`  
 \[out\] Zeichenfolge, die den Namen enthält.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Der angegebene Dokumentname unbekannt.|  
  
## Hinweise  
 Diese Methode gibt den angegebenen Dokumentnamen zurück.  
  
## Siehe auch  
 [IDebugDocumentInfo\-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE\-Enumeration](../../winscript/reference/documentnametype-enumeration.md)