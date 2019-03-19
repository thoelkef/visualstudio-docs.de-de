---
title: IRemoteDebugApplicationEx:RevokeBreak | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:RevokeBreak
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:RevokeBreak
ms.assetid: 1f077860-0a39-4ec9-b676-ae0712819c7b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0992eb5637434ccdf0dbf4fa6e436c87ae3fdd6c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148177"
---
# <a name="iremotedebugapplicationexrevokebreak"></a>IRemoteDebugApplicationEx:RevokeBreak

Widerruft einen Break-Befehl.

## <a name="syntax"></a>Syntax

```cpp
HRESULT RevokeBreak( );
```

### <a name="parameters"></a>Parameter

Keine

## <a name="return-value"></a>Rückgabewert

Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.

|Wert|Beschreibung|
|-----------|-----------------|
|`S_OK`|Die Methode war erfolgreich.|

## <a name="see-also"></a>Siehe auch

- [IRemoteDebugApplicationEx-Schnittstelle](iremotedebugapplicationex-interface.md)