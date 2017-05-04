---
title: "DOCUMENTNAMETYPE-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE-Enumeration"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DOCUMENTNAMETYPE-Enumeration
Beschreibt, die eingeben, die für ein Dokument abzurufen.  
  
## Syntax  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## Mitglieder  
  
|Member|Description|  
|------------|-----------------|  
|DOCUMENTNAMETYPE\_APPNODE|Ruft den Namen ab, wie sie in der Anwendungsstruktur angezeigt wird.|  
|DOCUMENTNAMETYPE\_TITLE|Ruft den Namen ab, während er auf der Viewertitelleiste angezeigt wird.|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|Ruft den Dateinamen ohne einen Pfad ab.|  
|DOCUMENTNAMETYPE\_URL|Ruft die URL des Dokuments ab.|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|Ruft den Namen ab, der mit Enumeration zur Identifikation angefügt wird.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)