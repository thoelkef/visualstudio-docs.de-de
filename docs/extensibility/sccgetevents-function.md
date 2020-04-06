---
title: SccGetEvents-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700817"
---
# <a name="sccgetevents-function"></a>SccGetEvents-Funktion
Diese Funktion ruft ein Statusereignis in der Warteschlange ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 lpFileName

[in, out] Puffer, bei dem das Quellcodeverwaltungs-Plug-In den zurückgegebenen Dateinamen (bis zu _MAX_PATH Zeichen) abgibt.

 lpStatus

[in, out] Gibt Statuscode zurück (siehe [Dateistatuscode](../extensibility/file-status-code-enumerator.md) für mögliche Werte).

 pnEventsRemaining

[in, out] Gibt die Anzahl der Einträge zurück, die nach diesem Aufruf in der Warteschlange verbleiben. Wenn diese Nummer groß ist, kann der Anrufer die [SccQueryInfo](../extensibility/sccqueryinfo-function.md) aufrufen, um alle Informationen auf einmal abzurufen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Get-Ereignisse erfolgreich.|
|SCC_E_OPNOTSUPPORTED|Diese Funktion wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird während der Verarbeitung im Leerlauf aufgerufen, um festzustellen, ob Statusaktualisierungen für Dateien unter Quellcodeverwaltung vorhanden sind. Das Quellcodeverwaltungs-Plug-In behält den Status aller bekannten Dateien bei, und wenn eine Statusänderung durch das Plug-In festgestellt wird, werden der Status und die zugehörige Datei in einer Warteschlange gespeichert. Wenn `SccGetEvents` aufgerufen wird, wird das oberste Element der Warteschlange abgerufen und zurückgegeben. Diese Funktion ist darauf beschränkt, nur zuvor zwischengespeicherte Informationen zurückzugeben und muss einen sehr schnellen Turnaround haben (d. h. kein Lesen des Datenträgers oder das Quellcodeverwaltungssystem nach Status fragen); Andernfalls kann die Leistung der IDE zu verschlechtern beginnen.

 Wenn keine Statusaktualisierung gemeldet werden soll, speichert das Quellcodeverwaltungs-Plug-In `lpFileName`eine leere Zeichenfolge im Puffer, auf den von verwiesen wird. Andernfalls speichert das Plug-In den vollständigen Pfadnamen der Datei, für die sich die Statusinformationen geändert haben, und gibt den entsprechenden Statuscode zurück (einer der im [Dateistatuscode](../extensibility/file-status-code-enumerator.md)beschriebenen Werte ).

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Dateistatuscode](../extensibility/file-status-code-enumerator.md)
