---
title: SccGetUserOption-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: eabf9cfc9d878d4d12096c8d264e8ee332031adf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353652"
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
 "pContext"

[in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.

 nOption

[in] Option zum Abrufen (mögliche Optionen finden Sie unter "Hinweise").

 lpVal

[out] Option zugeordnete Wert.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Option wurde erfolgreich abgerufen.|
|SCC_E_OPNOTSUPPORTED|Option wird nicht unterstützt.|
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|

## <a name="remarks"></a>Hinweise
 Die folgenden Optionen werden von dieser Befehl unterstützt:

|Benutzeroption|Beschreibung|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer möchte auf die lokale Version von Dateien auszuchecken. `lpVal` erhält `SCC_USEROPT_COLV_YES` (möchte Benutzer lokale Dateien auschecken) oder `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)