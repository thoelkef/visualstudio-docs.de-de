---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 968b204624662a1fb54d98703e163f76f0329adc
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205449"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Ruft einen Anzeigenamen für den Server ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
[out] Gibt einen Anzeigenamen für den Server zurück.

> [!NOTE]
> Der Aufrufer ist verantwortlich für das Freigeben der Zeichenfolge.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

## <a name="remarks"></a>Hinweise
 Für Benutzer-gestartet-Server ist der Name, der von dieser Methode zurückgegebene den vollständigen Namen des Servers. Bei Servern automatisch gestartet werden ist der Name des Computers an den Server ausgeführt wird, auf.

 Rufen Sie für den Namen der Computer-orientierten der [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)