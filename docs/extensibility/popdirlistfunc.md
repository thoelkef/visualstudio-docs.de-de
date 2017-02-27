---
title: "POPDIRLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "POPDIRLISTFUNC Callback-Funktion"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dies ist eine Rückruffunktion erhält die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Funktion eine Auflistung von Verzeichnissen und \(optional\) um herauszufinden, welche Quellcodeverwaltungsprojekt sind die Namen aktualisieren.  
  
 Die `POPDIRLISTFUNC` Rückruf aufgerufen werden, nur für die Verzeichnisse und Dateinamen \(in der Liste auf die `SccPopulateDirList` Funktion\), sind tatsächlich Quellcodeverwaltungsprojekt.  
  
## Signatur  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## Parameter  
 pvCallerData  
 \[in\] Benutzer angegebene Wert auf [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 auf bOrdneroptionen  
 \[in\] `TRUE` Wenn der Name in `lpDirectoryOrFileName` ist ein Verzeichnis; andernfalls der Name ist ein Dateiname.  
  
 lpDirectoryOrFileName  
 \[in\] Vollständige lokale Pfad zu einem Verzeichnis oder eine Datei an, der unter Quellcode ist.  
  
## Rückgabewert  
 Die IDE gibt einen geeigneten Fehlercode zurück:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Verarbeitung fortgesetzt.|  
|SCC\_I\_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC\_E\_xxx|Alle Fehler der entsprechenden Quelle Control soll Verarbeitung beendet werden.|  
  
## Hinweise  
 Wenn der `fOptions` Parameter von der `SccPopulateDirList` Funktion enthält die `SCC_PDL_INCLUDEFILES` kennzeichnen, und klicken Sie dann die Liste möglicherweise Dateinamen und Verzeichnisnamen enthalten wird.  
  
## Siehe auch  
 [Callback\-Funktionen, die von der IDE implementiert](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)