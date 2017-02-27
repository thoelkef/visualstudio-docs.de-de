---
title: "Befehl Code Enumerator | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehl Code enumerator"
  - "Source Control-Plug-ins Befehl Code-enumeration"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Befehl Code Enumerator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Enumerator wird verwendet, in den Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und die [SccPopulateList](../extensibility/sccpopulatelist-function.md)an, dass der Befehl für den Optionen angegeben werden.  
  
## Syntax  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## Mitglieder  
 SCC\_COMMAND\_GET  
 Entspricht der [SccGet](../extensibility/sccget-function.md).  
  
 SCC\_COMMAND\_CHECKOUT  
 Entspricht der [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC\_COMMAND\_CHECKIN  
 Entspricht der [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC\_COMMAND\_UNCHECKOUT  
 Entspricht der [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC\_COMMAND\_ADD  
 Entspricht der [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC\_COMMAND\_REMOVE  
 Entspricht der [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC\_COMMAND\_DIFF  
 Entspricht der [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC\_COMMAND\_HISTORY  
 Entspricht der [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC\_COMMAND\_RENAME  
 Entspricht der [SccRename](../extensibility/sccrename-function.md).  
  
 SCC\_COMMAND\_PROPERTIES  
 Entspricht der [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC\_COMMAND\_OPTIONS  
 Entspricht der [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)