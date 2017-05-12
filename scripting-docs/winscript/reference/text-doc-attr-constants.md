---
title: "TEXT_DOC_ATTR-Konstanten | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: 
  - "TEXT_DOC_ATTR-Konstanten"
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# TEXT_DOC_ATTR-Konstanten
Beschreiben Sie die Attribute des Dokuments.  
  
## Syntax  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## Konstanten  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|TEXT\_DOC\_ATTR\_READONLY|0x00000001|Das Dokument ist schreibgeschützt.|  
|TEXT\_DOC\_ATTR\_TYPE\_PRIMARY|0x00000002|Das Dokument wird die Grunddatei dieser Dokumentstruktur.|  
|TEXT\_DOC\_ATTR\_TYPE\_WORKER|0x00000004|Das Dokument ist ein Worker.|  
|TEXT\_DOC\_ATTR\_TYPE\_SCRIPT|0x00000008|Das Dokument wird eine Skriptdatei.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)