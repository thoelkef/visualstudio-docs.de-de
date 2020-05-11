---
title: SccEndBatch-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700927"
---
# <a name="sccendbatch-function"></a>SccEndBatch-Funktion
Diese Funktion schließt einen Batch von Quellcodeverwaltungsvorgängen ab. Diese Batches sind möglicherweise nicht geschachtelt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Batch von Operationen erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Quellcodeverwaltungsbatches werden verwendet, um dieselben Quellcodeverwaltungsvorgänge über mehrere Projekte oder mehrere Kontexte hinweg auszuführen. Batches können verwendet werden, um redundante Dialogfelder während eines Batchvorgangs aus der Benutzererfahrung zu entfernen. Der [SccBeginBatch](../extensibility/sccbeginbatch-function.md) `SccEndBatch` und die Funktion werden als Paar verwendet, um den Anfang und das Ende eines Vorgangs anzugeben. Sie können nicht verschachtelt werden.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
