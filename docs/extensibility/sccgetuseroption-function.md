---
title: Sccgetuseroption-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd024aa12b263eab7fea4bd80a0e77a3bbad5f1c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721441"
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

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Option wurde erfolgreich abgerufen.|
|SCC_E_OPNOTSUPPORTED|Die Option wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|

## <a name="remarks"></a>Hinweise
 Die folgenden Optionen werden von diesem Befehl unterstützt:

|Benutzer Option|Beschreibung|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer eine lokale Version der Dateien auschecken möchte. `lpVal` wird `SCC_USEROPT_COLV_YES` zugewiesen (der Benutzer möchte lokale Dateien Auschecken) oder `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)