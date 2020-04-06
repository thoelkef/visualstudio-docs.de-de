---
title: SccUncheckout-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700246"
---
# <a name="sccuncheckout-function"></a>SccUncheckout-Funktion
Diese Funktion macht einen vorherigen Auscheckvorgang auf und stellt so den Inhalt der ausgewählten Datei oder dateien in den Zustand vor dem Auschecken wieder her. Alle Änderungen, die seit dem Auschecken an der Datei vorgenommen wurden, gehen verloren.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 nFiles

[in] Anzahl der im `lpFileNames` Array angegebenen Dateien.

 lpFileNames

[in] Array voll qualifizierter lokaler Pfadnamen von Dateien, für die ein Auschecken rückgängig gemacht werden soll.

 Foptions

[in] Befehlsflags (nicht verwendet).

 pvOptions

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Rückgängig-Kasse war erfolgreich.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler. Die Rückgängig-Kasse war nicht erfolgreich.|
|SCC_E_NOTCHECKEDOUT|Der Benutzer hat die Datei nicht ausgecheckt.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht aus der Quellcodeverwaltung geöffnet.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|

## <a name="remarks"></a>Bemerkungen
 Nach diesem Vorgang `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` werden die und-Flags für die Dateien gelöscht, für die das Rückgängigmachen ausgeführt wurde.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
