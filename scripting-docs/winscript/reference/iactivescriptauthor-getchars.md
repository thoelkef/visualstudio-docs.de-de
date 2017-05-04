---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
Gibt den Satz von Abschlusszeichen für einen angeforderten Abschlusskontext zurück.  
  
## Syntax  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### Parameter  
 `fRequestedList`  
 \[in\] Der angeforderte Abschlusskontext.  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|Fordert die Enumeration der linken Seite.|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|Fordert den Memberabschlusskontext.|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|Fordert die Parameterliste.|  
|SCRIPT\_CMPL\_COMMIT|0x0004|Fordert Abschluss der Parameterliste.|  
  
 `pbstrChars`  
 \[out\] Die Zeichen, die zum angeforderten Abschlusskontext entsprechen.  
  
|`fRequestedList`\-Parameter|Zeichen zurückgegeben|  
|---------------------------------|---------------------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|"\="|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|\(","|  
|SCRIPT\_CMPL\_COMMIT|"\(\)"|  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)