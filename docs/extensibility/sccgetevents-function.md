---
title: SccGetEvents-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97c5c06a53214ef16924b50c4b35ee4bb33804ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433239"
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

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 lpFileName

[in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-In für die zurückgegebenen Dateinamen (bis zu _MAX_PATH-Zeichen) versetzt.

 lpStatus

[in, out] Gibt den Statuscode zurück (finden Sie unter [Datei Statuscode](../extensibility/file-status-code-enumerator.md) mögliche Werte).

 pnEventsRemaining

[in, out] Anzahl der Einträge in der Warteschlange verbleibt, nach dem Aufruf zurückgegeben. Wenn diese Zahl groß ist, könnten sich der Aufrufer zum Aufrufen der [SccQueryInfo](../extensibility/sccqueryinfo-function.md) um alle Informationen auf einmal abzurufen.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Ruft Ereignisse erfolgreich war.|
|SCC_E_OPNOTSUPPORTED|Diese Funktion wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Diese Funktion wird aufgerufen, während der Verarbeitung im Leerlauf befindet, um festzustellen, ob alle statusaktualisierungen für Dateien unter quellcodeverwaltung stattgefunden haben. Das Quellcodeverwaltungs-Plug-in verwaltet er den Status aller Dateien, die er kennt, und wenn eine Änderung des Status finden Sie durch das plug-in, den Status und die dazugehörige Datei in einer Warteschlange gespeichert werden. Wenn `SccGetEvents` aufgerufen wird, wird im oberen Bereich Element der Warteschlange abgerufen und zurückgegeben wird. Diese Funktion ist beschränkt, nur zuvor zwischengespeicherten Informationen zurückgegeben werden sollen, und benötigen einen sehr schnellen Turnaround (d. h. keine Lesen des Datenträgers oder Fragen das Quellcode-Verwaltungssystem für den Status) Andernfalls kann die Leistung der IDE gestartet, kann es zu Leistungseinbußen.

 Ist kein Update Status Bericht, speichert das Quellcodeverwaltungs-Plug-in eine leere Zeichenfolge in den Puffer, der auf `lpFileName`. Andernfalls das plug-in speichert den vollständigen Pfadnamen der Datei für die die Statusinformationen geändert hat, und gibt den entsprechenden Statuscode zurück (einen der Werte finden Sie im [Datei Statuscode](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Datei-Statuscode](../extensibility/file-status-code-enumerator.md)