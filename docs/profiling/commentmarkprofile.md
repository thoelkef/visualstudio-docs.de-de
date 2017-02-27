---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `CommentMarkProfile`\-Funktion fügt eine numerische Markierung und eine Textzeichenfolge in die VSP\-Datei ein.  Damit die Markierung und der Kommentar eingefügt werden, muss die Profilerstellung für den Thread, der die `CommentMarkProfile`\-Funktion enthält, auf ON festgelegt sein.  
  
## Syntax  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### Parameter  
 `lMarker`  
  
 Numerische Markierung, die eingefügt werden soll.  Diese muss größer oder gleich 0 \(null\) sein.  
  
 `szComment`  
  
 Zeiger auf die Textzeichenfolge, die eingefügt werden soll.  Die Zeichenfolge muss einschließlich des NULL\-Abschlusszeichens weniger als 256 Zeichen umfassen.  
  
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
 Der Profilerstellungszustand des Threads, der die Funktion zum Markieren von Profilen enthält, muss ON lauten, wenn Markierungen und Kommentare mit dem Mark\-Befehl von VSInstr oder mit Funktionen \(CommentMarkAtProfile, CommentMarkProfile oder MarkProfile\) eingefügt werden.  
  
 Profilmarkierungen weisen einen globalen Gültigkeitsbereich auf.  So kann beispielsweise eine Profilmarkierung, die in einem Thread eingefügt wurde, verwendet werden, um den Anfang oder das Ende eines Datensegments in einem beliebigen Thread in der VSP\-Datei zu markieren.  
  
> [!IMPORTANT]
>  Die CommentMarkProfile\-Methode kann nur mit der Instrumentation verwendet werden.  
  
## .NET Framework-Entsprechung  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informationen zur Funktion  
  
|||  
|-|-|  
|**Header**|VSPerf.h aufnehmen|  
|**Bibliothek**|VSPerf.lib verwenden|  
|**Unicode**|Implementiert als `CommentMarkProfileW` \(Unicode\) und `CommentMarkProfileA` \(ANSI\).|  
  
## Beispiel  
 Der folgende Code veranschaulicht den Aufruf der CommentMarkProfile\-Funktion.  Im Beispiel werden die Verwendung der Win32\-Zeichenfolgenmakros und die Compilereinstellungen für Unicode vorausgesetzt, um zu bestimmen, ob der Code die [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)]\-Funktion aufruft.  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Siehe auch  
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)