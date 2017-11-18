---
title: Migrieren von 64-Bit-Debugger COM+-Klassenregistrierungsdatenbank | Microsoft Docs
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.openlocfilehash: 06bfef5f1b4d67cb691a74b953296b1ab057d62f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrieren von 64-Bit-Debugger COM+-Klassenregistrierungsdatenbank

Debugger-Erweiterungen, die COM-Klassen in HKEY_CLASSES_ROOT (durch Verwendung Regasm "regsvr32", oder Schreiben direkt in die Registrierung) registrieren und geladenen msvsmon.exe Remotedebugger (), ist es jetzt möglich, ohne diese Registrierung mit Msvsmon bereitzustellen um zu HKEY_CLASSES_ROOT zu schreiben. Dies wirkt sich auf ältere .NET Debugger ausdruckauswertung oder Debugmodule, die konfiguriert sind, um in den msvsmon.exe-Prozess zu laden.

## <a name="msvsmon-comclass-def"></a>Msvsmon-Comclass-"def"

Um dieses Verfahren zu verwenden, fügen Sie eine Datei *.msvsmon-Comclass-def.json neben Msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Hier ist eine Beispiel Msvsmon-Comclass-Def-Datei, die eine verwaltete registriert und eine systemeigene Klasse:

Dateiname: MyCompany.MyExample.msvsmon-Comclass-def.json

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
