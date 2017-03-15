---
title: "Verwenden von Laufzeit&#252;berpr&#252;fungen ohne die C-Laufzeitbibliothek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CRT, Laufzeitüberprüfungen"
  - "Debugger, Systemeigene Laufzeitüberprüfungen"
  - "Debuggen [Visual Studio], Laufzeitroutinen"
  - "Laufzeitüberprüfungen, /RTC-Option"
  - "Laufzeitfehler, Fehlerüberprüfung"
  - "Laufzeitfehler, Laufzeitüberprüfungen"
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Verwenden von Laufzeit&#252;berpr&#252;fungen ohne die C-Laufzeitbibliothek
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie das Programm ohne die C\-Laufzeitbibliothek \(mit **\/NODEFAULTLIB**\) verknüpfen und Laufzeitfehlerüberprüfungen verwenden möchten, müssen Sie es mit RunTmChk.lib verknüpfen.  
  
 `_RTC_Initialize` initialisiert das Programm für Laufzeitüberprüfungen.  Wenn Sie keine Verknüpfung mit der C\-Laufzeitbibliothek erstellen, müssen Sie sicherstellen, dass das Programm mit Laufzeitüberprüfungen kompiliert wurde, bevor Sie `_RTC_Initialize` aufrufen:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Wenn Sie keine Verknüpfung mit der C\-Laufzeitbibliothek herstellen, müssen Sie außerdem eine Funktion mit der Bezeichnung `_CRT_RTC_INITW` definieren.  `_CRT_RTC_INITW` installiert die benutzerdefinierte Funktion folgendermaßen als Standardfehlerberichtsfunktion:  
  
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
  
 Nach der Installation der standardmäßigen Fehlerberichtsfunktion können Sie mit `_RTC_SetErrorFuncW` weitere Fehlerberichtsfunktionen installieren.  Weitere Informationen finden Sie unter [\_RTC\_SetErrorFuncW](/visual-cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## Siehe auch  
 [Gewusst wie: Verwenden von systemeigenen Laufzeitprüfungen](../debugger/how-to-use-native-run-time-checks.md)