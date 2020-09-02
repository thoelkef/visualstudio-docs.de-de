---
title: Befehls Code Enumerator | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f1a3f7146125e59d02efc72a4d4fc9ab33be39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184385"
---
# <a name="command-code-enumerator"></a>Befehlscodeenumerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Enumerator wird in den Optionen für [sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md) und [sccpopulatelist](../extensibility/sccpopulatelist-function.md)zum Angeben des Befehls verwendet, für den die Optionen angegeben werden.  
  
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
 Entspricht dem [sccget](../extensibility/sccget-function.md).  
  
 SCC_COMMAND_CHECKOUT  
 Entspricht dem [scccheckout](../extensibility/scccheckout-function.md).  
  
 SCC_COMMAND_CHECKIN  
 Entspricht dem [scccheckin](../extensibility/scccheckin-function.md).  
  
 SCC_COMMAND_UNCHECKOUT  
 Entspricht dem [sccuncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC_COMMAND_ADD  
 Entspricht dem [sccadd](../extensibility/sccadd-function.md)-.  
  
 SCC_COMMAND_REMOVE  
 Entspricht dem [SCUP](../extensibility/sccremove-function.md)-Vorgang.  
  
 SCC_COMMAND_DIFF  
 Entspricht dem [sccdiff](../extensibility/sccdiff-function.md).  
  
 SCC_COMMAND_HISTORY  
 Entspricht dem [scchistory](../extensibility/scchistory-function.md)-.  
  
 SCC_COMMAND_RENAME  
 Entspricht [sccrename](../extensibility/sccrename-function.md).  
  
 SCC_COMMAND_PROPERTIES  
 Entspricht den [sccproperties-Objekten](../extensibility/sccproperties-function.md).  
  
 SCC_COMMAND_OPTIONS  
 Entspricht der [sccsetoption](../extensibility/sccsetoption-function.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)   
 [Sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)
