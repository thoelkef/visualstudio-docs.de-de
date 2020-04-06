---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732401"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Diese Methode ruft eine [IDebugPortNotify2-Schnittstelle](../../../extensibility/debugger/reference/idebugportnotify2.md) für diesen Port ab.

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
[out] Ein [IDebugPortNotify2-Objekt.](../../../extensibility/debugger/reference/idebugportnotify2.md)

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Normalerweise wird `QueryInterface` die Methode für das Objekt aufgerufen, das die [IDebugPort2-Schnittstelle](../../../extensibility/debugger/reference/idebugport2.md) implementiert, um eine [IDebugPortNotify2-Schnittstelle](../../../extensibility/debugger/reference/idebugportnotify2.md) zu erhalten. Es gibt jedoch Umstände, in denen die gewünschte Schnittstelle für ein anderes Objekt implementiert wird. Diese Methode blendet diese `IDebugPortNotify2` Umstände aus und gibt die Schnittstelle aus dem am besten geeigneten Objekt zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
