---
title: SccAddFilesFromSCC Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc42a7be878ce52f4d951171c6b5cb08e195d564
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC-Funktion
Diese Funktion hinzugefügt zurzeit geöffneten Projekt eine Liste von Dateien aus der quellcodeverwaltung.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpUser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich null-Abschlusszeichen).  
  
 lpAuxProjPath  
 [in, out] Zusätzlichen Zeichenfolge, die zur Identifizierung des Projekts (bis zu `SCC_PRJPATH_`Größe, einschließlich null-Abschlusszeichen).  
  
 cFiles  
 [in] Anzahl der Dateien, die vom `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Array von Dateinamen, die das aktuelle Projekt hinzufügen.  
  
 lpDestination  
 [in] Der Zielpfad, in dem die Dateien werden geschrieben werden.  
  
 lpComment  
 [in] Der Kommentar auf einzelnen hinzugefügten Dateien angewendet werden soll.  
  
 pbResults  
 [in, out] Array von Flags, die auf Erfolg (ungleich NULL oder "true") festgelegt ist oder Fehler (0 (null) oder "false") für jede Datei (Größe des Arrays muss mindestens `cFiles` lang).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projekt ist nicht geöffnet werden.|  
|SCC_E_OPNOTPERFORMED|Verbindung ist nicht gemäß dem gleichen Projekt `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Benutzer ist nicht berechtigt, beim Aktualisieren der Datenbank.|  
|SCC_E_NONSPECIFICERROR|Unbekannter Fehler.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)