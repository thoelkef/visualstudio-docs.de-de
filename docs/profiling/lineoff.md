---
title: LineOff | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac671c3b0ba40c462403b2afa850c3936156d6d2
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774125"
---
# <a name="lineoff"></a>LineOff
Standardmäßig erfasst der Profiler die Zeilennummer des Quellcodes sowie die Offsetdaten der Zeilennummer, wenn Sie die Sampling-Profilerstellungsmethode verwenden. Die **LineOff**-Option für VSPerfCmd deaktiviert die Datensammlung der Zeilennummern, wenn VSPerfCmd zum Starten der Anwendung verwendet wird. Wenn **LineOff** angegeben ist, werden Profilerstellungsdaten für die Funktionsebene gesammelt.

 Sie können **LineOff** nur mit der Option **Launch** (Starten) verwenden und auch nur, wenn der Profiler für das Sampling mithilfe der Option **Start**:**Sample** initialisiert wurde.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parameter
 Keine

## <a name="required-options"></a>Erforderliche Optionen
 Die **LineOff**-Option kann nur auf einer Befehlszeile verwendet werden, die die Option **Launch** (Starten) enthält.

 **Launch:** `AppName` startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.

## <a name="example"></a>Beispiel
 In diesem Beispiel werden die Anwendung und der Profiler gestartet, und das Sampling auf Zeilenebene wird deaktiviert.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
