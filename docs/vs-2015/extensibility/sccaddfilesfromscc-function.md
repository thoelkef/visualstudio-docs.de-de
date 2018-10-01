---
title: SccAddFilesFromSCC-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5fbfdbfd926c3cd54f31f4b6b42d8baeacaff06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508984"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccAddFilesFromSCC-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccaddfilesfromscc-function).  
  
Diese Funktion hinzugefügt den aktuell geöffneten Projekt eine Liste von Dateien aus der quellcodeverwaltung.  
  
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
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpUser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des null-Abschlusszeichens).  
  
 lpAuxProjPath  
 [in, out] Zusätzliche Zeichenfolge, die zur Identifizierung des Projekts (bis zu `SCC_PRJPATH_`Größe, einschließlich des null-Abschlusszeichens).  
  
 cFiles  
 [in] Anzahl der Dateien, die vom `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Array von Dateinamen, die dem aktuellen Projekt hinzufügen.  
  
 lpDestination  
 [in] Der Zielpfad, wo sind die Dateien geschrieben werden.  
  
 lpComment  
 [in] Der Kommentar, der auf jede der hinzugefügten Dateien angewendet werden.  
  
 pbResults  
 [in, out] Array von Flags, die auf Erfolg (ungleich NULL oder "true") festgelegt ist oder Fehler (0 (null) oder "false") für jede Datei (Größe des Arrays muss mindestens `cFiles` lang).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projekt kann nicht geöffnet werden.|  
|SCC_E_OPNOTPERFORMED|Es ist keine Verbindung zum gleichen Projekt gemäß `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Benutzer ist nicht autorisiert, auf die Datenbank zu aktualisieren.|  
|SCC_E_NONSPECIFICERROR|Unbekannter Fehler.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)

