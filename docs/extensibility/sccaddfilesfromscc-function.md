---
title: SccAddFilesFromSCC-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701291"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC-Funktion
Diese Funktion fügt dem aktuell geöffneten Projekt eine Liste von Dateien aus der Quellcodeverwaltung hinzu.

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

### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpUser

[in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des Null-Terminators).

 lpAuxProjPath

[in, out] Hilfszeichenfolge zur Identifizierung des `SCC_PRJPATH_`Projekts (bis zu SIZE, einschließlich des Nullabschlusses).

 cFiles

[in] Anzahl der von `lpFilePaths`angegebenen Dateien.

 lpFilePaths

[in, out] Array von Dateinamen, die dem aktuellen Projekt hinzugefügt werden sollen.

 lpDestination

[in] Der Zielpfad, in dem die Dateien geschrieben werden sollen.

 lpComment

[in] Der Kommentar, der auf jede der hinzugefügten Dateien angewendet werden soll.

 pbErgebnisse

[in, out] Array von Flags, die so eingestellt sind, dass sie auf Erfolg (ungleich Null oder TRUE) `cFiles` oder Fehler (Null oder FALSE) für jede Datei hinweisen (die Größe des Arrays muss mindestens lang sein).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht geöffnet.|
|SCC_E_OPNOTPERFORMED|Die Verbindung ist nicht mit demselben Projekt verbunden, wie es von`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, die Datenbank zu aktualisieren.|
|SCC_E_NONSPECIFICERROR|Unknown error. (Unbekannter Fehler.)|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
