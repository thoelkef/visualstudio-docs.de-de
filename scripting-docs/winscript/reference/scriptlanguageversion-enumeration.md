---
title: "SCRIPTLANGUAGEVERSION-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTLANGUAGEVERSION-Enumeration
Gibt die möglichen Skripterstellungsversionen an.  
  
## Syntax  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|Die Standardversion.  Der ganzzahlige Wert ist 0.|  
|SCRIPTLANGUAGEVERSION\_5\_7|Windows, der Version 5.7 sowie.  Der ganzzahlige Wert ist 1.|  
|SCRIPTLANGUAGEVERSION\_5\_8|Windows, der Version 5.8 sowie.  Der ganzzahlige Wert ist 2.|  
|SCRIPTLANGUAGEVERSION\_MAX|Die maximale Version.  Der ganzzahlige Wert ist 255.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)