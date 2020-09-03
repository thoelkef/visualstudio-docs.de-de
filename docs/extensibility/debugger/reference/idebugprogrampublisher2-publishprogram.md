---
title: IDebugProgramPublisher2::P ublishprogram | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20de162bdc3be2cc4771c9746b13c40a1e140a96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721684"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Diese Methode stellt ein Programm für Debug-engines (des) und den Sitzungs-Debug-Manager zur Verfügung.

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
in Ein Array von GUIDs für des, das an dieses Programm gestartet oder angefügt werden kann.

`szFriendlyName`\
in Anzeige Name für das Programm (Dies wird in Menüs oder Dialogfeldern angezeigt, die dem Benutzer angezeigt werden).

`pDebuggeeInterface`\
[in] `IUnknown` Schnittstelle für das Programm (dieser Wert wird als Cookie verwendet, um das Programm eindeutig zu identifizieren; dieser Wert wird verwendet, um das Programm zu veröffentlichen).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Um ein Programm nicht mehr für das Debuggen verfügbar zu machen, nennen Sie [unpublishprogram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)
