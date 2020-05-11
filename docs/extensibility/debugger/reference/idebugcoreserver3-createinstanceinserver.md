---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733019"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Erstellt eine Instanz eines Debugmoduls auf dem Server.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parameter
`szDll`\
[in] Pfad zur DLL, die die im `clsidObject` Parameter angegebene CLSID implementiert. Wenn dies der Der Grund ist, `NULL`wird die Funktion von `CoCreateInstance` COM aufgerufen.

`wLangId`\
[in] Gebietsschema des Debugmoduls. Dies kann 0 sein, wenn die [SetLocale-Methode](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) nicht aufgerufen werden soll.

`clsidObject`\
[in] CLSID des zu erstellenden Debugmoduls.

`riid`\
[in] Schnittstellen-ID der spezifischen Schnittstelle, die vom Klassenobjekt abgerufen werden soll.

`ppvObject`\
[out] `IUnknown` Schnittstelle aus dem instanziierten Objekt. Cast oder marshallieren Sie dieses Objekt auf die gewünschte Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
