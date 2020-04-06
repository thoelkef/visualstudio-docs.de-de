---
title: SccBeginBatch-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701196"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch-Funktion
Diese Funktion startet eine Batchsequenz von Quellcodeverwaltungsvorgängen. Der [SccEndBatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch zu beenden. Diese Batches sind möglicherweise nicht geschachtelt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Batch von Vorgängen erfolgreich gestartet.|
|SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Quellcodeverwaltungsbatches werden verwendet, um dieselben Vorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder pro Projekt während eines Batchvorgangs aus der Benutzererfahrung zu entfernen. Die `SccBeginBatch` Funktion und der [SccEndBatch](../extensibility/sccendbatch-function.md) werden als Funktionspaar verwendet, um den Anfang und das Ende eines Vorgangs anzugeben. Sie können nicht verschachtelt werden. `SccBeginBatch`setzt ein Flag, das angibt, dass ein Stapelvorgang ausgeführt wird.

 Während ein Stapelvorgang ausgeführt wird, sollte das Quellcodeverwaltungs-Plug-In dem Benutzer höchstens ein Dialogfeld für jede Frage vorsehen und die Antwort aus diesem Dialogfeld auf alle nachfolgenden Vorgänge anwenden.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
