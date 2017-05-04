---
title: "SCRIPTTRACEINFO-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTTRACEINFO-Enumeration
Stellt das Skriptereignis dar, das aufgezeichnet wird.  Wird in [IActiveScriptSiteTraceInfo::SendScriptTraceInfo\-Methode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## Syntax  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|Der Anfang eines Skripts.|  
|SCRIPTTRACEINFO\_SCRIPTEND|Das Ende des Skripts.|  
|SCRIPTTRACEINFO\_COMCALLSTART|Der Beginn eines COM\-Aufrufs.|  
|SCRIPTTRACEINFO\_COMCALLEND|Das Ende eines COM\-Aufrufs.|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|Der Anfang der Objekterstellung.|  
|SCRIPTTRACEINFO\_CREATEOBJEND|Das Ende der Objekterstellung.|  
|SCRIPTTRACEINFO\_GETOBJSTART|Der Beginn eines GetObject\-Aufrufs.|  
|SCRIPTTRACEINFO\_GETOBJEND|Das Ende eines GetObject\-Aufrufs.|