---
title: Scccloseproject-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701051"
---
# <a name="scccloseproject-function"></a>Scccloseproject-Funktion
Diese Funktion schließt ein Projekt und markiert das Ende einer bestimmten Sitzung.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parameter
 pvcontext die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Projekt wurde erfolgreich geschlossen.|
|SCC_E_PROJNOTOPEN|Zurzeit ist kein Projekt geöffnet.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Das [sccopenproject](../extensibility/sccopenproject-function.md) wird immer vor dieser Funktion aufgerufen. Auf einen aufzurufenden Befehl folgt entweder die- `SccOpenProject` Funktion oder die [sccuninitialize](../extensibility/sccuninitialize-function.md)-Funktion, die die Verbindung mit dem Quell Code Verwaltungssystem vollständig beendet.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
