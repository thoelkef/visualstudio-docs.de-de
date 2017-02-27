---
title: "Directory Status Code Enumerator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Directory Status Code enumerator"
  - "Source Control-Plug-ins Verzeichnis Status-enumeration"
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Directory Status Code Enumerator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `SccDirStatus` Enumerator enthält benannte Konstante Werte, die den Status eines Verzeichnisses in das Quellcodeverwaltungssystem angeben. Diese Enumeration wird von [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md) verwendet. Dies wurde in Version 1.2 der Source Control\-Plug\-in\-API eingeführt.  
  
## Syntax  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## Mitglieder  
 SCC\_DIRSTATUS\_INVALID  
 Status konnte nicht abgerufen werden. verlassen Sie sich nicht darauf.  
  
 SCC\_DIRSTATUS\_NOTCONTROLLED  
 Verzeichnis ist nicht in einem Quellcodeverwaltungsprojekt.  
  
 SCC\_DIRSTATUS\_CONTROLLED  
 Verzeichnis ist in der quellcodeverwaltung.  
  
 SCC\_DIRSTATUS\_EMPTYPROJ  
 Projekt für dieses Verzeichnis ist leer.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)