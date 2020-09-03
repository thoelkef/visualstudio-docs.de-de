---
title: 'IDebugCoreServer3:: kreateingestanceinzuserver | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733019"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Erstellt eine Instanz einer Debug-Engine auf dem Server.

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
in Der Pfad zur dll, die die im-Parameter angegebene CLSID implementiert `clsidObject` . Wenn dieser Wert ist `NULL` , wird die com- `CoCreateInstance` Funktion aufgerufen.

`wLangId`\
in Das Gebiets Schema der Debug-Engine. Dies kann 0 sein, wenn die [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) -Methode nicht aufgerufen werden soll.

`clsidObject`\
in Die CLSID der zu erstellenden Debug-Engine.

`riid`\
in Die Schnittstellen-ID der spezifischen Schnittstelle, die aus dem Klassenobjekt abgerufen werden soll.

`ppvObject`\
[out] `IUnknown` Schnittstelle aus dem instanziierten Objekt. Wandelt oder marshallt dieses Objekt in die gewünschte Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
