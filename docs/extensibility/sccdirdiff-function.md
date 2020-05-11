---
title: SccDirDiff-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701011"
---
# <a name="sccdirdiff-function"></a>SccDirDiff-Funktion
Diese Funktion zeigt die Unterschiede zwischen dem aktuellen lokalen Verzeichnis auf dem Clientdatenträger und dem entsprechenden Projekt unter Quellcodeverwaltung an.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpDirName

[in] Vollständig qualifizierter Pfad zum lokalen Verzeichnis, für das ein visueller Unterschied angezeigt werden soll.

 dwFlags

[in] Befehlsflags (siehe Abschnitt "Bemerkungen").

 pvOptions

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Verzeichnis auf dem Datenträger ist mit dem Projekt in der Quellcodeverwaltung identisch.|
|SCC_I_FILESDIFFER|Das Verzeichnis auf dem Datenträger unterscheidet sich vom Projekt in der Quellcodeverwaltung.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|
|SCC_E_FILENOTCONTROLLED|Das Verzeichnis befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|
|SCC_E_FILENOTEXIST|Das lokale Verzeichnis wurde nicht gefunden.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird verwendet, um das Quellcodeverwaltungs-Plug-In anzuweisen, dem Benutzer eine Liste der Änderungen an einem angegebenen Verzeichnis anzuzeigen. Das Plug-In öffnet sein eigenes Fenster in einem Format seiner Wahl, um die Unterschiede zwischen dem Verzeichnis des Benutzers auf der Festplatte und dem entsprechenden Projekt unter Versionskontrolle anzuzeigen.

 Wenn ein Plug-In den Vergleich von Verzeichnissen unterstützt, muss es den Vergleich von Verzeichnissen auf Dateinamenbasis unterstützen, auch wenn die "Quick-Diff"-Optionen nicht unterstützt werden.

|`dwFlags`|Interpretation|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Fallunsensitive Vergleich (kann entweder für Quick Diff oder visual verwendet werden).|
|SCC_DIFF_IGNORESPACE|Ignoriert Leerraum (kann entweder für Quick-Diff oder Visual verwendet werden).|
|SCC_DIFF_QD_CONTENTS|Wenn vom Quellcodeverwaltungs-Plug-In unterstützt, wird das Verzeichnis automatisch byte byte verglichen.|
|SCC_DIFF_QD_CHECKSUM|Wenn vom Plug-In unterstützt, wird das Verzeichnis automatisch über eine Prüfsumme verglichen, oder, falls nicht unterstützt, auf SCC_DIFF_QD_CONTENTS zurück.|
|SCC_DIFF_QD_TIME|Wenn vom Plug-In unterstützt, vergleicht es das Verzeichnis automatisch über seinen Zeitstempel oder greift, falls nicht unterstützt, auf SCC_DIFF_QD_CHECKSUM oder SCC_DIFF_QD_CONTENTS zurück.|

> [!NOTE]
> Diese Funktion verwendet dieselben Befehlsflags wie [SccDiff](../extensibility/sccdiff-function.md). Ein Quellcodeverwaltungs-Plug-In kann jedoch die "Quick-Diff"-Operation für Verzeichnisse nicht unterstützen.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
