---
title: COM-Klassen Registrierung für 64-Bit-Debugger migrieren | Microsoft-Dokumentation
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62433694"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>COM-Klassen Registrierung für 64-Bit-Debugger migrieren

Bei Debugger-Erweiterungen, die com-Klassen in HKEY_CLASSES_ROOT registrieren, indem Regasm, regsvr32 oder direkt in die Registrierung geschrieben und in *msvsmon.exe* (der Remote Debugger) geladen werden, ist es jetzt möglich, diese Registrierung für msvsmon bereitzustellen, ohne in HKEY_CLASSES_ROOT schreiben zu müssen. Dies wirkt sich auf ältere .NET Debugger-Ausdrucksauswertungen oder debugengines aus, die für das Laden in den *msvsmon.exe* Prozess konfiguriert sind.

## <a name="msvsmon-comclass-def"></a>msvsmon-ComClass-DEF

Um dieses Verfahren zu verwenden, fügen Sie *neben msvsmon (INSTALLDIR: *.msvsmon-comclass-def.json* * \common7\ide\remotedebugger\x64 *) einen.msvsmon-comclass-def.jsfür die Datei hinzu.

Im folgenden finden Sie ein Beispiel für eine msvsmon-ComClass-DEF-Datei, die eine verwaltete und eine native Klasse registriert:

Dateiname: *MyCompany.MyExample.msvsmon-comclass-def.js*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
