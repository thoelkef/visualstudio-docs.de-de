---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 62033169e10585015b5f1439067aa0cbc42447a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754639"
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