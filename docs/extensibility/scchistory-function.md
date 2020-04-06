---
title: SccHistory-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700664"
---
# <a name="scchistory-function"></a>SccHistory-Funktion
Diese Funktion zeigt den Verlauf der angegebenen Dateien an.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parameter
 `pvContext`

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 `hWnd`

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 `nFiles`

[in] Anzahl der im `lpFileName` Array angegebenen Dateien.

 `lpFileName`

[in] Array vollqualifizierter Dateinamen.

 `fOptions`

[in] Befehlsflags (derzeit nicht verwendet).

 `pvOptions`

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Versionsverlauf wurde erfolgreich abgerufen.|
|SCC_I_RELOADFILE|Das Quellcodeverwaltungssystem hat die Datei tatsächlich auf dem Datenträger geändert, während der Verlauf abgerufen wurde (z. B. indem eine alte Version davon abgerufen wurde), daher sollte die IDE diese Datei neu laden.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht geöffnet.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler. Der Dateiverlauf konnte nicht abgerufen werden.|

## <a name="remarks"></a>Bemerkungen
 Das Quellcodeverwaltungs-Plug-In kann ein eigenes Dialogfeld anzeigen, `hWnd` um den Verlauf jeder Datei anzuzeigen, wobei das übergeordnete Fenster verwendet wird. Alternativ kann die optionale Textausgabe-Rückruffunktion, die dem [SccOpenProject](../extensibility/sccopenproject-function.md) zur Verfügung gestellt wird, verwendet werden, wenn sie unterstützt wird.

 Beachten Sie, dass sich die zu prüfende Datei unter bestimmten Umständen während der Ausführung dieses Aufrufs ändern kann. Der [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] Befehl history gibt dem Benutzer beispielsweise die Möglichkeit, eine alte Version der Datei zu erhalten. In einem solchen Fall kehrt das `SCC_I_RELOAD` Quellcodeverwaltungs-Plug-In zurück, um die IDE zu warnen, dass die Datei neu geladen werden muss.

> [!NOTE]
> Wenn das Quellcodeverwaltungs-Plug-In diese Funktion für ein Array von Dateien nicht unterstützt, kann nur der Dateiverlauf für die erste Datei angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
