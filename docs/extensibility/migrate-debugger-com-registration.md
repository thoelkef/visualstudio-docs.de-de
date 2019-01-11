---
title: Migrieren von 64-Bit-Debugger-COM-klassenregistrierung | Microsoft-Dokumentation
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 0b81d0dc38e4fb6c6bb14860634d41d85aa4dee9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892117"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrieren von 64-Bit-Debugger COM-klassenregistrierung

Debuggererweiterungen, die Registrierung von COM-Klassen in HKEY_CLASSES_ROOT unter Verwendung von Regasm "," regsvr32, oder Schreiben direkt in die Registrierung und in den geladen *msvsmon.exe* Remotedebugger (), es ist jetzt möglich, diesen bereitstellen "msvsmon" zum Schreiben in HKEY_CLASSES_ROOT ohne Registrierung. Dies wirkt sich auf älteren .NET Debugger ausdrucksauswertungen oder Debug-Engines, die konfiguriert sind, zum Laden von in die *msvsmon.exe* Prozess.

## <a name="msvsmon-comclass-def"></a>"msvsmon"-Comclass-def

Um dieses Verfahren verwenden, fügen einen  **.msvsmon-Comclass-def.json* Datei neben "msvsmon" (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Hier ist ein Beispiel für "msvsmon"-Comclass-Def-Datei, die verwaltet registriert, und eine native Klasse:

Dateiname: *MyCompany.MyExample.msvsmon-Comclass-def.json*

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
