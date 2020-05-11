---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fa3d111559a2c82fe36def202e5c1cf120c5202
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721588"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Macht ein Programm nicht für das Debuggen verfügbar.

## <a name="syntax"></a>Syntax

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parameter
`pDebuggeeInterface`\
[in] Eine `IUnknown` Schnittstelle zum Programm. Dies ist derselbe Wert, der der [PublishProgram-Methode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) zur Verfügung gestellt wird, und identifiziert das zu entfernende Programm eindeutig (d. h. es wird als Cookie verwendet).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Um ein Programm für die Debugmodule und den Sitzungsdebug-Manager verfügbar zu machen, verwenden Sie die [PublishProgram-Methode.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
