---
title: IDebugArrayField::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736311"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ruft den Rang oder die Anzahl der Dimensionen des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parameter
`pdwRank`\
[out] Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Rang eines Arrays entspricht der Anzahl der Dimensionen. In C++ und C' sind mehrdimensionale Arrays wirklich Arrays von Arrays und können `GetRank` daher nur als eindimensionales Array betrachtet werden (und die Methode gibt immer 1 zurück). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]hingegen werden mehrdimensionale Arrays unterschiedlich behandelt, und der Rang eines solchen Arrays gibt `GetRank` die Anzahl der Dimensionen an (und die Methode gibt immer die Anzahl der Dimensionen zurück).

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
