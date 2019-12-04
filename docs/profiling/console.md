---
title: Console | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6ec56665b546f962e8b3f4fd35460715390aee30
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777815"
---
# <a name="console"></a>Konsole
Die VSPerfCmd.exe-Option **Console** startet die angegebene Anwendung in einem neuen Eingabeaufforderungsfenster. **Console** kann nur mit der VSPerfCmd-Option **Launch** verwendet werden. Wenn die Anwendung keine Befehlszeilenanwendung ist, hat **Console** keine Auswirkungen.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parameter
 Keine

## <a name="required-options"></a>Erforderliche Optionen
 **Console** kann nur in einer Befehlszeile angegeben werden, die auch die Option **Launch** enthält.

 **Launch:** `AppName` startet den Profiler und die von `AppName` festgelegte Anwendung.

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
