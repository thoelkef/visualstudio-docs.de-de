---
title: IDebugField::Equal | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547311"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Diese Methode vergleicht dieses Feld mit dem angegebenen Feld hinsichtlich ihrer Gleichheit.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

#### <a name="parameters"></a>Parameter
 `pField`

 [in] Das Feld, in dieses Objekt verglichen werden soll.

## <a name="return-value"></a>Rückgabewert
 Gibt zurück, wenn die Felder identisch sind, `S_OK`. Gibt zurück, wenn die Felder unterscheiden, `S_FALSE.` wird, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)