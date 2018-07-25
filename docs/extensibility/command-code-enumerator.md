---
title: Befehl Dateistatuscode-Enumerator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67c133339f47a3f15822e4ff79587f9a09253a66
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231973"
---
# <a name="command-code-enumerator"></a>Befehlscodeenumerator
Dieser Enumerator wird verwendet, in den Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md)an, dass der Befehl für die die Optionen angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="members"></a>Member  
 SCC_COMMAND_GET  
 Entspricht der [SccGet](../extensibility/sccget-function.md).  
  
 SCC_COMMAND_CHECKOUT  
 Entspricht der [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC_COMMAND_CHECKIN  
 Entspricht der [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC_COMMAND_UNCHECKOUT  
 Entspricht der [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC_COMMAND_ADD  
 Entspricht der [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC_COMMAND_REMOVE  
 Entspricht der [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC_COMMAND_DIFF  
 Entspricht der [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC_COMMAND_HISTORY  
 Entspricht der [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC_COMMAND_RENAME  
 Entspricht der [SccRename](../extensibility/sccrename-function.md).  
  
 SCC_COMMAND_PROPERTIES  
 Entspricht der [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC_COMMAND_OPTIONS  
 Entspricht der [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)