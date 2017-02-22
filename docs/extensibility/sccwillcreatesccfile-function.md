---
title: "SccWillCreateSccFile-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "SccWillCreateSccFile-Funktion"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccWillCreateSccFile-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion bestimmt, ob das Quellcodeverwaltungs\-Plug\-in die Erstellung der MSSCCPRJ unterstützt. SCC\-Datei für die angegebenen Dateien.  
  
## Syntax  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 nFiles  
 \[in\] Die Anzahl der Dateinamen, die Bestandteil der `lpFileNames` sowie die Länge des Arrays der `pbSccFiles` Array.  
  
 lpFileNames  
 \[in\] Ein Array von vollqualifizierten Dateinamen überprüfen \(Arrays muss vom Aufrufer zugeordnet werden\).  
  
 pbSccFiles  
 \[in, out\] Ein Array zum Speichern der Ergebnisse.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Erfolgreich.|  
|SCC\_E\_INVALIDFILEPATH|Einer der Pfade im Array ist ungültig.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Diese Funktion wird aufgerufen, mit einer Liste von Dateien, um festzustellen, ob das Quellcodeverwaltungs\-Plug\-in in der MSSCCPRJ unterstützt. SCC\-Datei für die angegebenen Dateien \(für Weitere Informationen zu den MSSCCPRJ. SCC\-Datei finden Sie unter [MSSCCPRJ. SCC\-Datei](../extensibility/mssccprj-scc-file.md)\). Source Control\-Plug\-ins können deklariert werden, ob sie die Funktionen zum Erstellen von MSSCCPRJ aufweisen. SCC\-Dateien durch das Deklarieren `SCC_CAP_SCCFILE` während der Initialisierung. Das plug\-in gibt `TRUE` oder `FALSE` pro Datei in die `pbSccFiles` Array an, dass die angegebenen Dateien MSSCCPRJ haben. SCC\-Unterstützung. Wenn das plug\-in einen Erfolgscode aus der Funktion zurückgegeben wird, werden die Werte im zurückgegebenen Array berücksichtigt. Das Array wird ignoriert, bei einem Fehler.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ. SCC\-Datei](../extensibility/mssccprj-scc-file.md)