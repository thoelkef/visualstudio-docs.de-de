---
title: IDebugProgramPublisher2::PublishProgram | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d4f0b279bafe5291679237efdaada7907ddc515
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343375"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Auf diese Weise wird ein Programm für Debug-Engines (DEs) und sitzungsbasierter Debug-Manager.

## <a name="syntax"></a>Syntax

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

## <a name="parameters"></a>Parameter
`Engines`\
[in] Ein Array von GUIDs für DEs, die gestartet oder angehängt werden, um dieses Programm kann.

`szFriendlyName`\
[in] Der Anzeigename für das Programm (Dies wird in Menüs oder dem Benutzer angezeigten Dialogfelder angezeigt).

`pDebuggeeInterface`\
[in] `IUnknown` Schnittstelle für das Programm (dieser Wert wird als ein Cookie verwendet, um die Anwendung eindeutig zu identifizieren, der gleiche Wert wird verwendet, das Programm "Veröffentlichung")

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Um ein Programm nicht mehr für das Debuggen verfügbar machen, rufen Sie [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Siehe auch
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)