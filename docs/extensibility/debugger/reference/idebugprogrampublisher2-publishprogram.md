---
title: IDebugProgramPublisher2::PublishProgram | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1553070f9afecf6ce60ac51b94ecb3f05d0eb9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698767"
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

#### <a name="parameters"></a>Parameter
 `Engines`

 [in] Ein Array von GUIDs für DEs, die gestartet oder angehängt werden, um dieses Programm kann.

 `szFriendlyName`

 [in] Der Anzeigename für das Programm (Dies wird in Menüs oder dem Benutzer angezeigten Dialogfelder angezeigt).

 `pDebuggeeInterface`

 [in] `IUnknown` Schnittstelle für das Programm (dieser Wert wird als ein Cookie verwendet, um die Anwendung eindeutig zu identifizieren, der gleiche Wert wird verwendet, das Programm "Veröffentlichung")

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Um ein Programm nicht mehr für das Debuggen verfügbar machen, rufen Sie [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Siehe auch
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)