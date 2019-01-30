---
title: PROFILE_CURRENTID | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bad393dafc2aae0476b4986554b2a02c919e074
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985236"
---
# <a name="profilecurrentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID gibt das Pseudotoken für die Thread-ID oder die Prozess-ID in einem Aufruf der Funktionen NameProfile, StartProfile, StopProfile, SuspendProfile und ResumeProfile zurück. Verwenden Sie das Token, damit die Funktion den aktuellen Thread oder Prozess verarbeitet anstatt eines ausdrücklich angegebenen.  
  
## <a name="example"></a>Beispiel  
 PROFILE_CURRENTID wird in *VSPerf.h* wie folgt definiert:  
  
```cpp  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## <a name="example"></a>Beispiel  
 PROFILE_CURRENTID wird anhand des folgenden Beispiels veranschaulicht. Das Beispiel verwendet PROFILE_CURRENTID als Parameter, der den aktuellen Thread in einem Aufruf der [StartProfile](../profiling/startprofile.md)-Funktion identifiziert.  
  
```cpp  
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
  
## <a name="see-also"></a>Siehe auch  
 [Referenz für Profiler-APIs in Visual Studio (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)