---
title: IDebugReference2::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetSize
helpviewer_keywords:
- IDebugReference2::GetSize
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5512a9d07c859dc548f91611bfc8d0c05621c0ff
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329782"
---
# <a name="idebugreference2getsize"></a>IDebugReference2::GetSize
Ruft die Größe in Bytes, der den Wert des Verweises an. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Parameter
`pdwSize`\
[out] Gibt die Größe in Bytes, der den Wert des Verweises zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)