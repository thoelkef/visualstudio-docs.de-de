---
title: IDebugProgram2::GetENCUpdate | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 363018d13cfeee1691881f4d8b814cdd0b2dfa35
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212339"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Diese Methode ruft das Update bearbeiten und Fortfahren "(ENC) für dieses Programm an. Eine benutzerdefinierten Debug-Engine gibt immer `E_NOTIMPL`.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parameter
`ppUpdate`\
[out] Gibt eine interne Schnittstelle, die zum Aktualisieren dieses Programms verwendet werden kann.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Eine benutzerdefinierten Debug-Engine sollte immer zurückgeben `E_NOTIMPL`.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)