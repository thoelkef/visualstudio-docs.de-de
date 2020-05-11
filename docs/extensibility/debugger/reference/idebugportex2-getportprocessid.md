---
title: IDebugPortex2::GetPortProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae974461e312c68e6fcc14150a08879ac7709950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725134"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Ruft die Prozess-ID des Ports selbst ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>Parameter
`pdwProcessId`\
[out] Gibt die physische Prozess-ID des Ports selbst zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In der Win32-Laufzeit ruft diese Methode z. `GetCurrentProcessId` B. in der Regel die Win32-Funktion auf, um die physische Prozess-ID abzuruft.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
