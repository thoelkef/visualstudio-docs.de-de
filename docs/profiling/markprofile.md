---
title: "MarkProfile | Microsoft Docs"
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
  - "MarkProfile"
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# MarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der `MarkProfile`\-Methode wird eine Profilmarkierung in die VSP\-Datei eingefügt.  Damit die Markierung eingefügt wird, muss die Profilerstellung für den Thread, der die `MarkProfile`\-Funktion enthält, auf ON festgelegt sein.  
  
## Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### Parameter  
 `lMarker`  
  
 Die einzufügende Markierung.  Diese muss größer oder gleich 0 \(null\) sein.  
  
## Eigenschaftswert\/Rückgabewert  
 Die Funktion gibt mit der **PROFILE\_COMMAND\_STATUS**\-Enumeration Erfolg oder Fehler an.  Folgende Rückgabewerte sind möglich:  
  
|Enumerator|**Beschreibung**|  
|----------------|----------------------|  
|MARK\_ERROR\_MARKER\_RESERVED|Der Parameter ist kleiner oder gleich 0.  Diese Werte sind reserviert.  Die Markierung und der Kommentar werden nicht aufgezeichnet.|  
|MARK\_ERROR\_MODE\_NEVER|Der Profilerstellungsmodus wurde beim Aufrufen der Funktion auf NEVER festgelegt.  Die Markierung und der Kommentar werden nicht aufgezeichnet.|  
|MARK\_ERROR\_MODE\_OFF|Der Profilerstellungsmodus wurde beim Aufrufen der Funktion auf OFF festgelegt.  Die Markierung und der Kommentar werden nicht aufgezeichnet.|  
|MARK\_ERROR\_NO\_SUPPORT|In diesem Kontext werden keine Markierungen unterstützt.  Die Markierung und der Kommentar werden nicht aufgezeichnet.|  
|MARK\_ERROR\_OUTOFMEMORY|Es war kein Arbeitsspeicher zum Aufzeichnen des Ereignisses verfügbar.  Die Markierung und der Kommentar werden nicht aufgezeichnet.|  
|MARK\_TEXTTOOLONG|Die Zeichenfolge überschreitet die maximale Länge von 256 Zeichen.  Die Kommentarzeichenfolge wird abgeschnitten, und die Markierung und der Kommentar werden aufgezeichnet.|  
|MARK\_OK|Bei Erfolg wird MARK\_OK zurückgegeben.|  
  
## Hinweise  
 Der bei jeder Ausführung des Codes in die VSP\-Datei eingefügte Markierungswert, wenn für den Thread, der die MarkProfile\-Funktion enthält, ein Profil erstellt wird.  Sie können MarkProfile mehrmals aufrufen.  
  
 Profilmarkierungen weisen einen globalen Gültigkeitsbereich auf.  So kann beispielsweise eine Profilmarkierung, die in einem Thread eingefügt wurde, verwendet werden, um den Anfang oder das Ende eines Datensegments in einem beliebigen Thread in der VSP\-Datei zu markieren.  
  
 Der Profilerstellungszustand des Threads, der die Funktion zum Markieren von Profilen enthält, muss ON lauten, wenn Markierungen und Kommentare mit dem Mark\-Befehl oder mit API\-Funktionen \(CommentMarkAtProfile, CommentMarkProfile oder MarkProfile\) eingefügt werden.  
  
> [!IMPORTANT]
>  Die MarkProfile\-Methode sollte nur mit der instrumentierten Profilerstellung verwendet werden.  
  
## .NET Framework-Entsprechung  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informationen zur Funktion  
 Header: In VSPerf.h deklariert  
  
 Importbibliothek: VSPerf.lib  
  
## Beispiel  
 Der folgende Code veranschaulicht die MarkProfile\-Funktion.  
  
```  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Siehe auch  
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)