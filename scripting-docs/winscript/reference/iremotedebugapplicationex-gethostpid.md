---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d660cce006e7f84f1b1c01f1ec0a406b5c4b9df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934585"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Gibt die Prozess-ID für die hostanwendung zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Parameter

`dwHostPid`

[out] Die Host-Prozess-ID an.

## <a name="return-value"></a>Rückgabewert

Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.

|Wert|Beschreibung|
|-----------|-----------------|
|`S_OK`|Die Methode war erfolgreich.|

## <a name="remarks"></a>Hinweise

Wird von der IDE verwendet.

## <a name="see-also"></a>Siehe auch

- [IRemoteDebugApplicationEx-Schnittstelle](iremotedebugapplicationex-interface.md)