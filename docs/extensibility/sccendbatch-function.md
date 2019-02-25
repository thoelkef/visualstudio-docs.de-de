---
title: SccEndBatch-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0662e4c4d1d71e2c9ae0e8f40ff21868d6b9a5d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683921"
---
# <a name="sccendbatch-function"></a>SccEndBatch-Funktion
Diese Funktion ist einen Batch von Quellcodeverwaltungsvorgänge abgeschlossen. Diese Batches können nicht geschachtelt werden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Batches von Vorgängen, die erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Source-Control-Batches werden verwendet, um die gleichen Quellcodeverwaltungsvorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder über die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die [SccBeginBatch](../extensibility/sccbeginbatch-function.md) und `SccEndBatch` Funktion dienen als ein paar Anfang und Ende eines Vorgangs an. Sie sind nicht schachtelbar.

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)