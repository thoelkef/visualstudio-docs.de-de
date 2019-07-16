---
title: SccGetExtendedCapabilities-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa6a067a0b9e8358f503228dbc53e20586b84468
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353667"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities-Funktion
Diese Funktion gibt die zusätzliche Funktionen, die von das Quellcodeverwaltungs-Plug-in unterstützt werden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parameter
 "pContext"

[in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.

 lSccExCaps

[in] Ein Flag, das eine erweiterte Funktion, die zu überprüfende angibt (siehe die Tabelle erweiterte Funktion Code im [funktionsflags](../extensibility/capability-flags.md) für die möglichen Flags).

 pbSupported

[out] Ungleich NULL zurück (`TRUE`) Wenn die angegebene Funktion unterstützt wird; andernfalls wird NULL (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Der Vorgang des Get-Funktion, die erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Unbekannte oder nicht angegebene Fehler ist aufgetreten.|

## <a name="remarks"></a>Hinweise
 Diese Methode wird bei Bedarf aufgerufen. also wenn eine Funktion getestet werden muss, wird diese Methode aufgerufen, um zu bestimmen, ob, die Funktion unterstützt wird. Nur ein Flag zu einem Zeitpunkt angegeben wird.

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Fehlercodes](../extensibility/error-codes.md)
- [Funktionsflags](../extensibility/capability-flags.md)