---
title: Migrieren von 64-Bit-Debugger-COM-klassenregistrierung | Microsoft-Dokumentation
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712202"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrieren von 64-Bit-Debugger COM-klassenregistrierung

Debuggererweiterungen, die Registrierung von COM-Klassen in HKEY_CLASSES_ROOT unter Verwendung von Regasm "," regsvr32, oder Schreiben direkt in die Registrierung und in den geladen *msvsmon.exe* Remotedebugger (), es ist jetzt möglich, diesen bereitstellen "msvsmon" zum Schreiben in HKEY_CLASSES_ROOT ohne Registrierung. Dies wirkt sich auf älteren .NET Debugger ausdrucksauswertungen oder Debug-Engines, die konfiguriert sind, zum Laden von in die *msvsmon.exe* Prozess.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Um dieses Verfahren verwenden, fügen einen  **.msvsmon-Comclass-def.json* Datei neben "msvsmon" (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Hier ist ein Beispiel für "msvsmon"-Comclass-Def-Datei, die verwaltet registriert, und eine native Klasse:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.json*

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
