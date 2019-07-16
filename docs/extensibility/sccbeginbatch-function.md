---
title: SccBeginBatch-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6bb145358184117046e14b7b598ce6d4bb4586b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333887"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch-Funktion
Diese Funktion wird eine Batch-Sequenz von Quellcodeverwaltungsvorgänge gestartet. Die [SccEndBatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch beenden. Diese Batches können nicht geschachtelt werden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Batches von Vorgängen wurde erfolgreich gestartet.|
|SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Source-Control-Batches werden verwendet, um die gleichen Vorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante projektbezogene Dialogfeldern auf die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die `SccBeginBatch` Funktion und die [SccEndBatch](../extensibility/sccendbatch-function.md) dienen als Funktionspaar Anfang und Ende eines Vorgangs an. Sie sind nicht schachtelbar. `SccBeginBatch` Legt ein Flag, der angibt, dass ein Batchvorgang ausgeführt wird.

 Während ein Batchvorgangs aktiviert ist, sollte das Quellcodeverwaltungs-Plug-in höchstens ein Dialogfeld für Fragen an den Benutzer vorhanden und die Antwort in diesem Dialogfeld auf alle nachfolgenden Operationen anwenden.

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)