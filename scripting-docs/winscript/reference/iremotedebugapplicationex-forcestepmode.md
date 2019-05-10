---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 04a2c700d2cac4bcdc845ebf442de29863e87deb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934639"
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