---
title: SccQueryInfo-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700482"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo-Funktion
Diese Funktion ruft Statusinformationen für eine Gruppe ausgewählter Dateien unter Quellcodeverwaltung ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 nFiles

[in] Anzahl der im `lpFileNames` Array angegebenen Dateien `lpStatus` und der Länge des Arrays.

 lpFileNames

[in] Ein Array von Namen von Dateien, die abgefragt werden sollen.

 lpStatus

[in, out] Ein Array, in dem das Quellcodeverwaltungs-Plug-In die Statusflags für jede Datei zurückgibt. Weitere Informationen finden Sie unter [Dateistatuscode](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Abfrage war erfolgreich.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem vorliegt, das wahrscheinlich durch Netzwerk- oder Konfliktprobleme verursacht wurde. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht unter Quellcodeverwaltung geöffnet.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Wenn `lpFileName` es sich um eine leere Zeichenfolge handelt, sind derzeit keine Statusinformationen zu aktualisieren. Andernfalls ist es der vollständige Pfadname der Datei, für die sich die Statusinformationen möglicherweise geändert haben.

 Das Rückgabe-Array kann eine `SCC_STATUS_xxxx` Bitmaske von Bits sein. Weitere Informationen finden Sie unter [Dateistatuscode](../extensibility/file-status-code-enumerator.md). Ein Quellcodeverwaltungssystem unterstützt möglicherweise nicht alle Bittypen. Wenn z. `SCC_STATUS_OUTOFDATE` B. nicht angeboten wird, wird das Bit einfach nicht festgelegt.

 Beachten Sie bei Verwendung dieser Funktion `MSSCCI` zum Auschecken von Dateien die folgenden Statusanforderungen:

- `SCC_STATUS_OUTBYUSER`wird festgelegt, wenn der aktuelle Benutzer die Datei ausgecheckt hat.

- `SCC_STATUS_CHECKEDOUT`kann nicht `SCC_STATUS_OUTBYUSER` festgelegt werden, es sei denn, es wird festgelegt.

- `SCC_STATUS_CHECKEDOUT`wird nur festgelegt, wenn die Datei in das angegebene Arbeitsverzeichnis ausgecheckt wird.

- Wenn die Datei vom aktuellen Benutzer in ein anderes Verzeichnis als `SCC_STATUS_OUTBYUSER` das `SCC_STATUS_CHECKEDOUT` Arbeitsverzeichnis ausgecheckt ist, ist festgelegt, aber nicht.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Dateistatuscode](../extensibility/file-status-code-enumerator.md)
