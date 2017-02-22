---
title: "SccAddFilesFromSCC-Funktion | Microsoft Docs"
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
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "SccAddFilesFromSCC-Funktion"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAddFilesFromSCC-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion fügt eine Liste von Dateien aus Datenquellen\-Steuerelement dem aktuell geöffneten Projekt.  
  
## Syntax  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 \[in, out\] Der Benutzername \(bis zu SCC\_USER\_SIZE, einschließlich null\-Abschlusszeichen\).  
  
 lpAuxProjPath  
 \[in, out\] Zusätzliche Zeichenfolge, die zur Identifizierung des Projekts \(bis zu `SCC_PRJPATH_`Größe, einschließlich null\-Abschlusszeichen\).  
  
 cFiles  
 \[in\] Anzahl der Dateien, die vom `lpFilePaths`.  
  
 lpFilePaths  
 \[in, out\] Array von Dateinamen für das aktuelle Projekt hinzufügen.  
  
 lpDestination  
 \[in\] Der Zielpfad, in dem die Dateien geschrieben werden.  
  
 lpComment  
 \[in\] Der Kommentar, der auf die hinzugefügte Dateien angewendet werden.  
  
 pbResults  
 \[in, out\] Array von Flags, die auf Erfolg \(ungleich NULL oder TRUE\) oder Fehler \(0 \(null\) oder "false"\) für jede Datei \(Größe des Arrays muss mindestens `cFiles` lang\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_E\_PROJNOTOPEN|Projekt ist nicht geöffnet.|  
|SCC\_E\_OPNOTPERFORMED|Verbindung ist nicht gemäß einem Projekt `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|Benutzer ist nicht autorisiert, um die Datenbank zu aktualisieren.|  
|SCC\_E\_NONSPECIFICERROR|Ein Fehler aufgetreten.|  
|SCC\_I\_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)