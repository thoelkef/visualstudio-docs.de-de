---
title: SccCloseProject-Funktion | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701051"
---
# <a name="scccloseproject-function"></a>SccCloseProject-Funktion
Diese Funktion schließt ein Projekt und markiert das Ende einer bestimmten Sitzung.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parameter
 pvContext Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Projekt wurde erfolgreich abgeschlossen.|
|SCC_E_PROJNOTOPEN|Derzeit ist kein Projekt geöffnet.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Das [SccOpenProject](../extensibility/sccopenproject-function.md) wird immer vor dieser Funktion aufgerufen. Auf einen Aufruf dieser Funktion folgt dann `SccOpenProject` ein Aufruf der Funktion oder der [SccUninitialize](../extensibility/sccuninitialize-function.md), die die Verbindung zum Quellcodeverwaltungssystem vollständig beendet.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
