---
title: SccGetUserOption-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700689"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption-Funktion
Diese Funktion ruft eine Vielzahl von benutzerspezifischen Optionen ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 nOption

[in] Option zum Abrufen (siehe Hinweise zu möglichen Optionen).

 lpVal

[out] Wert, der der Option zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Option wurde erfolgreich abgerufen.|
|SCC_E_OPNOTSUPPORTED|Option wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Die folgenden Optionen werden von diesem Befehl unterstützt:

|Benutzeroption|BESCHREIBUNG|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer die lokale Version von Dateien auschecken möchte. `lpVal`zugewiesen `SCC_USEROPT_COLV_YES` (Benutzer möchte lokale Dateien auschecken) oder `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)
