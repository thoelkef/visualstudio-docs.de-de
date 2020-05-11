---
title: SccDirQueryInfo-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700954"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo-Funktion
Diese Funktion untersucht eine Liste voll qualifizierter Verzeichnisse auf ihren aktuellen Status.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parameter
 pContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 nDirs

[in] Die Anzahl der zu abgefragten Verzeichnisse.

 lpDirNames

[in] Ein Array voll qualifizierter Pfade der abzugefragten Verzeichnisse.

 lpStatus

[in, out] Eine Arraystruktur für das Quellcodeverwaltungs-Plug-In zum Zurückgeben der Statusflags (Details finden Sie unter [Verzeichnisstatuscode).](../extensibility/directory-status-code-enumerator.md)

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Abfrage war erfolgreich.|
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Die Funktion füllt das Rückgabearray mit einer `SCC_DIRSTATUS` Bitmaske von Bits aus der Familie (siehe [Verzeichnisstatuscode](../extensibility/directory-status-code-enumerator.md)), einem Eintrag für jedes angegebene Verzeichnis. Das Status-Array wird vom Aufrufer zugewiesen.

 Die IDE verwendet diese Funktion, bevor ein Verzeichnis umbenannt wird, um zu überprüfen, ob das Verzeichnis unter Quellcodeverwaltung steht, indem sie abfragt, ob es über ein entsprechendes Projekt verfügt. Wenn sich das Verzeichnis nicht unter Quellcodeverwaltung befindet, kann die IDE dem Benutzer die richtige Warnung geben.

> [!NOTE]
> Wenn ein Quellcodeverwaltungs-Plug-In einen oder mehrere Statuswerte nicht implementiert, sollten nicht implementierte Bits auf Null gesetzt werden.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Verzeichnisstatuscode](../extensibility/directory-status-code-enumerator.md)
