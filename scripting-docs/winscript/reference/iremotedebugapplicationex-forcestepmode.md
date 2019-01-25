---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb5c94c55709f5ecdbd6bae63ee3366f3dfeb2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790853"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

Erzwingt, dass den Debugger in einschrittigen Modus.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>Parameter

`pStepThread`

[in] Thread für die schrittweise des Prozessmonitors Debuggen. Wenn der Wert null ist, löscht das PDM schrittweisen Threads.

## <a name="return-value"></a>Rückgabewert

Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.

|Wert|Beschreibung|
|-----------|-----------------|
|`S_OK`|Die Methode war erfolgreich.|

## <a name="see-also"></a>Siehe auch

- [IRemoteDebugApplicationEx-Schnittstelle](iremotedebugapplicationex-interface.md)