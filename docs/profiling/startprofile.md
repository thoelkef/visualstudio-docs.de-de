---
title: "StartProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `StartProfile`\-Funktion legt den Indikator für die angegebene Profilebene auf 1 \(ON\) fest.  
  
## Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### Parameter  
 `Level`  
  
 Gibt die Profilebene an, auf der Leistungsdaten erfasst werden können.  Mithilfe der folgenden **PROFILE\_CONTROL\_LEVEL**\-Enumeratoren kann eine der drei Ebenen für die Erfassung von Leistungsdaten angegeben werden:  
  
|Enumerator|**Beschreibung**|  
|----------------|----------------------|  
|PROFILE\_GLOBALLEVEL|Die Festlegung auf die globale Ebene wirkt sich auf alle Prozesse und Threads der Profilerstellung aus.|  
|PROFILE\_PROCESSLEVEL|Die Festlegung auf die Prozessebene wirkt sich auf alle Threads aus, die Teil des angegebenen Prozesses sind.|  
|PROFILE\_THREADLEVEL|Die Festlegung auf die Threadprofilerstellungs\-Ebene wirkt sich auf den angegebenen Thread aus.|  
  
 `dwId`  
  
 Der vom System generierte Prozess\- oder Threadbezeichner.  
  
## Eigenschaftswert\/Rückgabewert  
 Die Funktion gibt mit der **PROFILE\_COMMAND\_STATUS**\-Enumeration Erfolg oder Fehler an.  Folgende Rückgabewerte sind möglich:  
  
|Enumerator|**Beschreibung**|  
|----------------|----------------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|Die Profilelement\-ID ist nicht vorhanden.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|Die angegebene Profilebene ist nicht vorhanden.|  
|PROFILE\_ERROR\_MODE\_NEVER|Der Profilerstellungsmodus wurde beim Aufrufen der Funktion auf NEVER festgelegt.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|Der Funktionsaufruf für die Profilerstellung, die Profilebene oder die Kombination von Aufruf und Ebene ist noch nicht implementiert.|  
|PROFILE\_OK|Der Aufruf wurde erfolgreich ausgeführt.|  
  
## Hinweise  
 Durch StartProfile und StopProfile wird der Start\/Stop\-Zustand für die Profilebene gesteuert.  Der Standardwert von Starten\/Beenden ist 1.  Der Anfangswert kann in der Registrierung geändert werden.  Durch jeden Aufruf von StartProfile wird Start\/Stop auf 1 festgelegt, während durch jeden Aufruf von StopProfile Start\/Stop auf 0 \(null\) festgelegt wird.  
  
 Wenn Start\/Stop größer als 0 \(null\) ist, lautet der Start\/Stop\-Zustand für die Ebene ON.  Ist der Wert kleiner oder gleich 0 \(null\), lautet der Start\/Stop\-Zustand OFF.  
  
 Wenn sowohl der Start\/Stop\-Zustand als auch der Suspend\/Resume\-Zustand ON lautet, ist auch der Profilerstellungszustand für die Ebene auf ON festgelegt.  Wenn ein Profil für einen Thread erstellt werden soll, muss der Zustand des Threads sowohl auf der globalen Ebene als auch auf der Prozessebene und der Threadebene ON lauten.  
  
## .NET Framework-Entsprechung  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informationen zur Funktion  
 Header: In VSPerf.h deklariert  
  
 Importbibliothek: VSPerf.lib  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht den Aufruf der StartProfile\-Funktion.  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Siehe auch  
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)