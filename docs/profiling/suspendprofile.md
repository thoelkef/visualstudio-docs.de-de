---
title: "SuspendProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SuspendProfile"
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SuspendProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `SuspendProfile`\-Methode inkrementiert den Suspend\/Resume\-Zähler für die angegebene Profilebene.  
  
## Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
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
 Der Anfangswert des Suspend\/Resume\-Indikators ist 0.  Jeder Aufruf von SuspendProfile fügt der Suspend\/Resume\-Anzahl 1 hinzu; jeder Aufruf von ResumeProfile subtrahiert 1.  
  
 Wenn die Suspend\/Resume\-Anzahl größer als 0 \(null\) ist, lautet der Suspend\/Resume\-Zustand für die Ebene OFF.  Ist die Anzahl kleiner oder gleich 0 \(null\), lautet der Suspend\/Resume\-Zustand ON.  
  
 Wenn sowohl der Start\/Stop\-Zustand als auch der Suspend\/Resume\-Zustand ON lautet, ist auch der Profilerstellungszustand für die Ebene auf ON festgelegt.  Wenn ein Profil für einen Thread erstellt werden soll, muss der Zustand des Threads sowohl auf der globalen Ebene als auch auf der Prozessebene und der Threadebene ON lauten.  
  
## .NET Framework-Entsprechung  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informationen zur Funktion  
 Header: In VSPerf.h deklariert  
  
 Importbibliothek: VSPerf.lib  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die SuspendProfile\-Methode.  In diesem Beispiel wird davon ausgegangen, dass ein vorheriger Aufruf von StartProfile für den durch [PROFILE\_CURRENTID](../profiling/profile-currentid.md) identifizierten Prozess oder Thread erfolgt ist.  
  
```  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Siehe auch  
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)