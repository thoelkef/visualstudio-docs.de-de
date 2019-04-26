---
title: Ausgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78d5b39908bc0ffa39533c22ea4effcbe97397b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794216"
---
# <a name="output"></a>Output
Die Option **Ausgabe** gibt den Namen der Profilerstellungsdaten für die Leistungssitzung an. **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parameter
 `FileName`: der Name der Datendatei. Es werden vollständige und partielle Pfade angenommen. Wenn kein Pfad angegeben ist, wird die Datei im aktuellen Verzeichnis erstellt.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.

 **Start:** `Method` gibt den Ausgabedateinamen an.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Profilerstellungs-Datendatei im aktuellen Verzeichnis erstellt.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)