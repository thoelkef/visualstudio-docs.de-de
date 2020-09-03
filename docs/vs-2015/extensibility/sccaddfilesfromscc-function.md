---
title: Sccaddfilesfromscc-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200907"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion fügt eine Liste von Dateien aus der Quell Code Verwaltung dem aktuell geöffneten Projekt hinzu.  
  
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
 pContext  
 in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 lpuser  
 [in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Terminator).  
  
 lpauxprojpath  
 [in, out] Zusätzliche Zeichenfolge, die das Projekt identifiziert (bis zur `SCC_PRJPATH_` Größe, einschließlich des NULL-Terminator).  
  
 cFiles  
 in Anzahl von Dateien, die von angegeben werden `lpFilePaths` .  
  
 lpfilepath  
 [in, out] Array von Dateinamen, die dem aktuellen Projekt hinzugefügt werden sollen.  
  
 lpdestination  
 in Der Zielpfad, in den die Dateien geschrieben werden sollen.  
  
 lpcomment  
 in Der Kommentar, der auf jede der hinzugefügten Dateien angewendet werden soll.  
  
 pbresults  
 [in, out] Ein Array von Flags, die festgelegt werden, um einen Erfolg (ungleich 0 oder true) oder einen Fehler (null oder false) für jede Datei anzugeben (die Größe des Arrays muss mindestens `cFiles` lang sein).  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht geöffnet.|  
|SCC_E_OPNOTPERFORMED|Die Verbindung ist nicht mit dem Projekt identisch, das von angegeben wird. `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, die Datenbank zu aktualisieren.|  
|SCC_E_NONSPECIFICERROR|Unbekannter Fehler.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
