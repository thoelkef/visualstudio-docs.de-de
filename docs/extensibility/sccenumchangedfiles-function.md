---
title: "SccEnumChangedFiles-Funktion | Microsoft Docs"
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
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "SccEnumChangedFiles-Funktion"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccEnumChangedFiles-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erhalten eine Liste von lokalen Dateien, bestimmt diese Funktion, welche Dateien in der Quellcode\-Verwaltungsdatenbank Code die entsprechenden Versionen unterscheiden.  
  
## Syntax  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 cFiles  
 \[in\] Anzahl der im angegebenen Dateinamen der `lpFileNames` Array. Gibt auch die Größe des `plIsFileDifferent` Array.  
  
 lpFileNames  
 \[in\] Array der Namen der lokalen Datei zu überprüfen.  
  
 plIsFileDifferent  
 \[in, out\] Array von Werten, die den Unterschied Status jeder Datei \(Array benötigen mindestens `cFiles` Einträge\). Ungleich NULL bedeutet, dass sich die Datei unterscheidet.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Der Vorgang wurde erfolgreich abgeschlossen.|  
|SCC\_UNSPECIFIEDERROR|Allgemeiner Fehler.|  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)