---
title: IDebugBreakpointChecksumRequest2::IsChecksumEnabled | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ffcf1e576efe371a848061e0b5e5828943c6ed9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210850"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
Bestimmt, ob die Prüfsumme für dieses Dokument aktiviert ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsChecksumEnabled(
   BOOL *pfChecksumEnabled
);
```

```csharp
public int IsChecksumEnabled(
   out int pfChecksumEnabled
);
```

## <a name="parameters"></a>Parameter
`pfChecksumEnabled`\
[out] Gibt TRUE zurück, wenn die Prüfsumme aktiviert ist. Andernfalls wird FALSE zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)