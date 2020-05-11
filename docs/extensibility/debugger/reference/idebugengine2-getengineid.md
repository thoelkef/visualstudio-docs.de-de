---
title: IDebugEngine2::GetEngineID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4071e8279c2c4ab615ff625c1bbedebfd8e64ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731081"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Ruft die GUID des Debugmoduls (DE) ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Parameter
`pguidEngine`\
[out] Gibt die GUID der DE zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Einige Beispiele für typische `guidScriptEng`GUIDs sind , `guidNativeEng`oder `guidSQLEng`. Neue Debug-Engines erstellen eine eigene GUID zur Identifizierung.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CEngine` Methode für ein einfaches Objekt implementiert wird, das die [IDebugEngine2-Schnittstelle](../../../extensibility/debugger/reference/idebugengine2.md) implementiert.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
