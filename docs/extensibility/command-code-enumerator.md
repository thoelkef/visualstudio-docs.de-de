---
title: Befehl Dateistatuscode-Enumerator | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4ec14c15bbd0aa6340e30e3156e714ba5f9e074
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334964"
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
SCC_COMMAND_GET entspricht der [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT entspricht der [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN entspricht der [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT entspricht der [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD entspricht der [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE entspricht der [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF entspricht der [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY entspricht der [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME entspricht der [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES entspricht der [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS entspricht der [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
