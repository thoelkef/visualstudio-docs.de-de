---
title: 'IDebugDefaultPort2:: getportnotify | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732401"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Diese Methode ruft eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) -Schnittstelle für diesen Port ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parameter
`ppPortNotify`\
vorgenommen Ein [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) -Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Normalerweise wird die- `QueryInterface` Methode für das Objekt aufgerufen, das die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle implementiert, um eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) -Schnittstelle abzurufen. Es gibt jedoch Situationen, in denen die gewünschte Schnittstelle auf einem anderen Objekt implementiert wird. Diese Methode verbirgt diese Umstände und gibt die- `IDebugPortNotify2` Schnittstelle aus dem am besten geeigneten-Objekt zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
