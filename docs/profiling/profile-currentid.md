---
title: "PROFILE_CURRENTID | Microsoft Docs"
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
  - "PROFILE_CURRENTID"
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

PROFILE\_CURRENTID gibt das Pseudotoken für die Thread\- oder Prozess\-ID in einem Aufruf der NameProfile\-Funktion, StartProfile\-Funktion, StopProfile\-Funktion, SuspendProfile\-Funktion und ResumeProfile\-Funktion zurück.  Verwenden Sie PROFILE\_CURRENTID, um die Funktion für den aktuellen Thread oder Prozess und nicht für einen ausdrücklich genannten Thread oder Prozess zu verwenden.  
  
## Beispiel  
 PROFILE\_CURRENTID wird in VSPerf.h wie folgt definiert:  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht PROFILE\_CURRENTID.  Darin wird PROFILE\_CURRENTID als Parameter verwendet, der den aktuellen Thread in einem Aufruf der [StartProfile](../profiling/startprofile.md)\-Funktion identifiziert.  
  
```  
void ExerciseProfileCurrentID()  
{  
    // Declare ProfileOperationResult enumeration   
    // to hold return value of a call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    profileResult = StartProfile(  
        PROFILE_GLOBALLEVEL,  
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
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)