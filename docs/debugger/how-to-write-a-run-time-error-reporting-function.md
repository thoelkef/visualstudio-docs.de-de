---
title: "Gewusst wie: Schreiben einer Berichtsfunktion f&#252;r Laufzeitfehler | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
  - "Berichtsfunktion"
  - "Laufzeitfehler, Berichtsfunktionen"
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Schreiben einer Berichtsfunktion f&#252;r Laufzeitfehler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine benutzerdefinierte Berichtsfunktion für Laufzeitfehler muss die gleiche Deklaration wie `_CrtDbgReportW` aufweisen.  Die Funktion muss den Wert 1 an den Debugger zurückgeben.  
  
 Im folgenden Beispiel wird das Definieren einer benutzerdefinierten Berichtsfunktion dargestellt.  
  
## Beispiel  
  
```  
#include <stdio.h>  
int errorhandler = 0;  
void configureMyErrorFunc(int i)  
{  
    errorhandler = i;  
}  
  
int MyErrorFunc(int errorType, const wchar_t *filename,  
                int linenumber, const wchar_t *moduleName,  
                const wchar_t *format, ...)  
{  
    switch (errorhandler)  
    {  
    case 0:  
    case 1:  
        wprintf(L"Error type %d at %s line %d in %s",  
                errorType, filename, linenumber, moduleName);  
        break;  
    case 2:  
    case 3:  
        fprintf(stderr, "Error type");  
        break;  
    }  
  
    return 1;  
}  
```  
  
## Beispiel  
 Im folgenden Beispiel wird eine komplexere benutzerdefinierte Berichtsfunktion dargestellt.  In diesem Beispiel behandelt die `switch`\-Anweisung entsprechend der Definition durch den `reportType`\-Parameter von `_CrtDbgReportW` verschiedene Fehlertypen.  Da Sie `_CrtDbgReportW` ersetzen, können Sie `_CrtSetReportMode` nicht verwenden.  Die Funktion muss die Ausgabe behandeln.  Das erste Variablenargument in dieser Funktion nimmt eine Laufzeitfehlernummer an.  Weitere Informationen finden Sie unter [\_RTC\_SetErrorType](/visual-cpp/c-runtime-library/reference/rtc-seterrortype).  
  
```  
#include <windows.h>  
#include <stdarg.h>  
#include <rtcapi.h>  
#include <malloc.h>  
#pragma runtime_checks("", off)  
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,   
                   const wchar_t *module, const wchar_t *format, ...)  
{  
    // Prevent re-entrance.  
    static long running = 0;  
    while (InterlockedExchange(&running, 1))  
        Sleep(0);  
    // Now, disable all RTC failures.  
    int numErrors = _RTC_NumErrors();  
    int *errors=(int*)_alloca(numErrors);  
    for (int i = 0; i < numErrors; i++)  
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);  
  
   // First, get the rtc error number from the var-arg list.  
    va_list vl;  
    va_start(vl, format);  
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);  
    va_end(vl);  
  
    wchar_t buf[512];  
    const char *err = _RTC_GetErrDesc(rtc_errnum);  
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",  
        err,  
        line,  
        file ? file : L"Unknown",  
        module ? module : L"Unknown");  
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;  
    // Now, restore the RTC errortypes.  
    for(int i = 0; i < numErrors; i++)  
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);  
    running = 0;  
    return res;  
}  
#pragma runtime_checks("", restore)  
```  
  
## Beispiel  
 Um anstelle von `_CrtDbgReportW` die benutzerdefinierte Funktion zu installieren, verwenden Sie `_RTC_SetErrorFuncW`.  Weitere Informationen finden Sie unter [\_RTC\_SetErrorFuncW](/visual-cpp/c-runtime-library/reference/rtc-seterrorfuncw).  Der Rückgabewert von `_RTC_SetErrorFuncW` ist die vorherige Berichtsfunktion, die Sie bei Bedarf speichern und wiederherstellen können.  
  
```  
#include <rtcapi.h>  
int main()  
{  
    _RTC_error_fnW oldfunction, newfunc;  
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);  
    // Run some code.  
    newfunc = _RTC_SetErrorFuncW(oldfunction);  
    // newfunc == &MyErrorFunc;  
    // Run some more code.  
}  
```  
  
## Siehe auch  
 [Anpassen der systemeigenen Laufzeitüberprüfung](../debugger/native-run-time-checks-customization.md)