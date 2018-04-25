---
title: Zur Laufzeit mithilfe von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 533e4254b6222af1713691a0c448cad1383cd273
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Verwenden von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek
Wenn Sie das Programm ohne die C-Laufzeitbibliothek verknüpfen, verwenden **/NODEFAULTLIB**, und laufzeitfehlerüberprüfungen verwenden möchten, müssen Sie mit RunTmChk.lib verknüpfen.  
  
 `_RTC_Initialize` initialisiert das Programm für Laufzeitüberprüfungen. Wenn Sie keine Verknüpfung mit der C-Laufzeitbibliothek erstellen, müssen Sie sicherstellen, dass das Programm mit Laufzeitüberprüfungen kompiliert wurde, bevor Sie `_RTC_Initialize` aufrufen:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Wenn Sie keine Verknüpfung mit der C-Laufzeitbibliothek herstellen, müssen Sie außerdem eine Funktion mit der Bezeichnung `_CRT_RTC_INITW` definieren. `_CRT_RTC_INITW` installiert die benutzerdefinierte Funktion folgendermaßen als Standardfehlerberichtsfunktion:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Nach der Installation der standardmäßigen Fehlerberichtsfunktion können Sie mit `_RTC_SetErrorFuncW` weitere Fehlerberichtsfunktionen installieren. Weitere Informationen finden Sie unter [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwenden von nativen Laufzeitprüfungen](../debugger/how-to-use-native-run-time-checks.md)