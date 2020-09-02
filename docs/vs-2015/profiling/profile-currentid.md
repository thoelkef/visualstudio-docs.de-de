---
title: PROFILE_CURRENTID | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42ac8c5d7c00be51b3accc662fb0ffb52b5bfab3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198056"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PROFILE_CURRENTID gibt das Pseudotoken für die Thread-ID oder die Prozess-ID in einem Aufruf der Funktionen NameProfile, StartProfile, StopProfile, SuspendProfile und ResumeProfile zurück. Verwenden Sie das Token, damit die Funktion den aktuellen Thread oder Prozess verarbeitet anstatt eines ausdrücklich angegebenen.  
  
## <a name="example"></a>Beispiel  
 PROFILE_CURRENTID wird in VSPerf.h wie folgt definiert:  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## <a name="example"></a>Beispiel  
 PROFILE_CURRENTID wird anhand des folgenden Beispiels veranschaulicht. Das Beispiel verwendet PROFILE_CURRENTID als Parameter, der den aktuellen Thread in einem Aufruf der [StartProfile](../profiling/startprofile.md)-Funktion identifiziert.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Profiler-API-Referenz (nativ)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Name profile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [Start profile](../profiling/startprofile.md)   
 [Stop profile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)
