---
title: SccGetExtendedCapabilities-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700726"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities-Funktion
Diese Funktion gibt zusätzliche Funktionen zurück, die vom Quellcodeverwaltungs-Plug-In unterstützt werden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 lSccExCaps

[in] Ein Flag, das eine erweiterte Funktion angibt, für die getestet werden soll (siehe die Tabelle Extended Capability Code in [Capability-Flags](../extensibility/capability-flags.md) für die möglichen Flags).

 pbUnterstützt

[out] Gibt einen Wert`TRUE`ungleich Null zurück ( ), wenn die angegebene Funktion unterstützt wird; Andernfalls wird Null`FALSE`zurückgegeben ( ).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Get-Fähigkeitsvorgang wurde erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Unbekannter oder nicht angegebener Fehler ist aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird bei Bedarf aufgerufen; Wenn also eine Funktion getestet werden muss, wird diese Methode aufgerufen, um zu bestimmen, ob diese Funktion unterstützt wird. Es wird jeweils nur ein Flag angegeben.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)
- [Fähigkeitsflags](../extensibility/capability-flags.md)
