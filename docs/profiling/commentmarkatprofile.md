---
title: "CommentMarkAtProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der `CommentMarkAtProfile`\-Methode werden ein Timestampwert, eine numerische Markierung und eine Kommentarzeichenfolge in die VSP\-Datei eingefügt.  Der Timestampwert kann verwendet werden, um externe Ereignisse zu synchronisieren.  Damit die Markierung und der Kommentar eingefügt werden, muss die Profilerstellung für den Thread, der die CommentMarkAtProfile\-Funktion enthält, auf ON festgelegt sein.  
  
## Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### Parameter  
 `dnTimestamp`  
  
 Eine 64\-Bit\-Ganzzahl, die einen Timestampwert darstellt.  
  
 `lMarker`  
  
 Die numerische Markierung, die eingefügt werden soll.  Diese muss größer oder gleich 0 \(null\) sein.  
  
 `szComment`  
  
 Ein Zeiger auf die Textzeichenfolge, die eingefügt werden soll.  Die Zeichenfolge muss einschließlich des NULL\-Abschlusszeichens weniger als 256 Zeichen umfassen.  
  
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
 Der Profilerstellungszustand des Threads, der die Funktion zum Markieren von Profilen enthält, muss ON lauten, wenn Markierungen und Kommentare mit dem Mark\-Befehl oder mit API\-Funktionen \(CommentMarkAtProfile, CommentMarkProfile oder MarkProfile\) eingefügt werden.  Profilmarkierungen weisen einen globalen Gültigkeitsbereich auf.  So kann beispielsweise eine Profilmarkierung, die in einem Thread eingefügt wurde, verwendet werden, um den Anfang oder das Ende eines Datensegments in einem beliebigen Thread in der VSP\-Datei zu markieren.  
  
> [!IMPORTANT]
>  CommentMarkAtProfile\-Methoden sollten nur mit der Instrumentation verwendet werden.  
  
## .NET Framework-Entsprechung  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informationen zur Funktion  
  
|||  
|-|-|  
|**Header**|VSPerf.h aufnehmen|  
|**Bibliothek**|VSPerf.lib verwenden|  
|**Unicode**|Implementiert als CommentMarkAtProfileW \(Unicode\) und CommentMarkAtProfileA \(ANSI\).|  
  
## Beispiel  
 Der folgende Code veranschaulicht den Aufruf der generischen CommentMarkAtProfile\-Funktion.  Im Beispiel werden die Verwendung der Win32\-Zeichenfolgenmakros und die Compilereinstellungen für ANSI vorausgesetzt, um zu bestimmen, ob der Code die ANSI\-fähige Funktion aufruft.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Siehe auch  
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)