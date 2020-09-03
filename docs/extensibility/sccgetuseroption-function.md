---
title: Sccgetuseroption-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700689"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption-Funktion
Diese Funktion Ruft eine Vielzahl Benutzer spezifischer Optionen ab.

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

in Der Kontext Zeiger für das Quellcodeverwaltungs-Plug-in.

 noption

in Die abzurufende Option (siehe Hinweise zu möglichen Optionen).

 lpval

vorgenommen Wert, der Option zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Option wurde erfolgreich abgerufen.|
|SCC_E_OPNOTSUPPORTED|Die Option wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Die folgenden Optionen werden von diesem Befehl unterstützt:

|Benutzer Option|BESCHREIBUNG|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer eine lokale Version der Dateien auschecken möchte. `lpVal` wird zugewiesen `SCC_USEROPT_COLV_YES` (Benutzer möchte lokale Dateien Auschecken) oder `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)
