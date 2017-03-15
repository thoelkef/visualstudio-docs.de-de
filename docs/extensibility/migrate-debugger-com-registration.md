---
title: Migrieren von 64-Bit-Debugger COM+-Klassenregistrierungsdatenbank | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e273f31cb1f43ff79fd9a4ade37d112351dea9b5
ms.lasthandoff: 02/22/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrieren von 64-Bit-Debugger COM+-Klassenregistrierungsdatenbank

>**Hinweis:** diese Dokumentation ist vorläufig und basierend auf der Visual Studio 2017 RC-Version.

Debugger-Erweiterungen, die COM-Klassen in HKEY_CLASSES_ROOT (durch Regasm regsvr32 verwenden oder direkt in die Registrierung schreiben) registrieren und geladenen msvsmon.exe (remote Debugger) ist es möglich, diese Registrierung mit Msvsmon bereitzustellen, ohne in HKEY_CLASSES_ROOT zu schreiben. Dies wirkt sich auf ältere .NET Debugger ausdrucksauswertungen oder Debugmodule, die zum Laden des Prozesses msvsmon.exe konfiguriert sind.

## <a name="msvsmon-comclass-def"></a>Msvsmon-Comclass-def

Um dieses Verfahren zu verwenden, fügen Sie eine Datei *.msvsmon-Comclass-def.json neben Msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Hier ist ein Beispiel Msvsmon-Comclass-Def-Datei, die eine verwaltete registriert, und eine systemeigene Klasse:

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

