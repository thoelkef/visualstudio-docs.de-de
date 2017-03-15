---
title: "NameProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der `NameProfile`\-Funktion wird dem angegebenen Prozess oder Thread eine Zeichenfolge zugewiesen.  
  
 Die NameProfile\-API ist nur für die instrumentierte Profilerstellung verfügbar.  Die NameProfile\-API wird nicht für die Sampling\-Profilerstellung unterstützt.  
  
## Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### Parameter  
 `pszName`  
  
 Der Name des Profilelements.  Ein Name ist unter folgenden Voraussetzungen ungültig \(was dazu führt, dass NameProfileA NAME\_ERROR\_INVALID\_NAME zurückgibt\):  
  
-   Der in NameProfileA übergebene Zeiger ist ein NULL\-Wert.  
  
-   Die Zeichenfolgendaten von pszName beginnen mit einer Zahl.  
  
-   Die Zeichenfolgendaten von pszName enthalten ein Leerzeichen.  
  
-   Die von Zeichenfolgendaten pszName enthalten beliebigen der folgenden Zeichen: ,;.\`~\!@\#$%^&\*\(\)\=\[\]{}&#124;\\?\/\<\>  
  
 `Level`  
  
 Gibt die Profilebene an, auf der Leistungsdaten erfasst werden können.  Mithilfe der folgenden **PROFILE\_CONTROL\_LEVEL**\-Werte kann eine der drei Ebenen für die Erfassung von Leistungsdaten angegeben werden:  
  
|Enumerator|**Beschreibung**|  
|----------------|----------------------|  
|PROFILE\_GLOBALLEVEL|Die Festlegung auf die globale Ebene wirkt sich auf alle Prozesse und Threads der Profilerstellung aus.|  
|PROFILE\_PROCESSLEVEL|Die Festlegung auf die Prozessebene wirkt sich auf alle Threads aus, die Teil des angegebenen Prozesses sind.|  
|PROFILE\_THREADLEVEL|Die Festlegung auf die Threadprofilerstellungs\-Ebene wirkt sich auf den angegebenen Thread aus.|  
  
 `dwId`  
  
 Bezeichner der Profilebene.  Verwenden Sie den vom System generierten Prozess\- oder Threadbezeichner.  
  
## Eigenschaftswert\/Rückgabewert  
 Die Funktion gibt mit der **PROFILE\_COMMAND\_STATUS**\-Enumeration Erfolg oder Fehler an.  Folgende Rückgabewerte sind möglich:  
  
|Enumerator|**Beschreibung**|  
|----------------|----------------------|  
|NAME\_ERROR\_ID\_NOEXIST|Das angegebene Profilelement ist nicht vorhanden.|  
|NAME\_ERROR\_INVALID\_NAME|Der Name ist ungültig.|  
|NAME\_ERROR\_LEVEL\_NOEXIST|Die angegebene Profilebene ist nicht vorhanden.|  
|NAME\_ERROR\_NO\_SUPPORT|Der angegebene Vorgang wird nicht unterstützt.|  
|NAME\_ERROR\_OUTOFMEMORY|Es war kein Arbeitsspeicher zum Aufzeichnen des Ereignisses verfügbar.|  
|NAME\_ERROR\_REDEFINITION|Dem Profilelement wurde bereits ein Name zugewiesen.  Der Name in dieser Funktion wird ignoriert.|  
|NAME\_ERROR\_TEXTTRUNCATED|Der Text des Namens hat die maximale Länge von 32 Zeichen einschließlich des NULL\-Zeichens überschritten und wurde deshalb abgeschnitten.|  
|NAME\_OK|Der Name wurde erfolgreich registriert.|  
  
## Hinweise  
 Jedem Prozess oder Thread kann nur ein Name zugewiesen werden.  Nachdem einem Profilelement ein Name zugeordnet worden ist, werden nachfolgende Aufrufe von NameProfile für dieses Element ignoriert.  
  
 Wird verschiedenen Threads oder Prozessen derselbe Name zugewiesen, enthält der Bericht Daten von allen Elementen dieses Namens auf der betreffenden Ebene.  
  
 Wenn Sie einen anderen als den aktuellen Prozess oder Thread angeben, müssen Sie sicherstellen, dass dieser initialisiert und gestartet wurde, bevor Sie einen Namen zuweisen.  Andernfalls schlägt die NameProfile\-Methode fehl.  
  
> [!IMPORTANT]
>  Die CreateProcess\(\)\-API\-Funktion und die CreateThread\(\)\-API\-Funktion können zurückgegeben werden, bevor der Thread oder Prozess initialisiert wird.  
  
## .NET Framework-Entsprechung  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informationen zur Funktion  
  
|||  
|-|-|  
|**Header**|VSPerf.h aufnehmen|  
|**Bibliothek**|VSPerf.lib verwenden|  
|**Unicode**|Implementiert als `NameProfileW` \(Unicode\) und `NameProfileA` \(ANSI\).|  
  
## Beispiel  
 Der folgende Code veranschaulicht den Aufruf der NameProfile\-Funktion.  Im Beispiel werden die Verwendung der Win32\-Zeichenfolgenmakros und die Compilereinstellungen für ANSI vorausgesetzt, um zu bestimmen, ob der Code die ANSI\-fähige Funktion aufruft.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Siehe auch  
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)