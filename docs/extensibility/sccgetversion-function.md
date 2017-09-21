---
title: "SccGetVersion-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetVersion"
helpviewer_keywords: 
  - "SccGetVersion-Funktion"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetVersion-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft die Versionsnummer der Source\-Plug\-in\-API mit dem durch das Quellcodeverwaltungs\-Plug\-in unterstützt.  
  
## Syntax  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### Parameter  
 Keine.  
  
## Rückgabewert  
 Ein `LONG` \-Datentyp, der die Versionsnummer der unterstützten APIs an Source Control\-Plug\-in enthält:  
  
|WORD|Beschreibung|  
|----------|------------------|  
|HIWORD|Hauptversion|  
|LOWORD|Nebenversion|  
  
## Hinweise  
 Wenn ein Quellcodeverwaltungs\-Plug\-in, Version 1.3 der Source Control\-Plug\-in\-API unterstützt, wird diese Funktion z. B. 0x0103 zurück.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)