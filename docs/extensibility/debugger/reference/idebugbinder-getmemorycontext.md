---
title: IDebugBinder::GetMemoryContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7c647f12e80adab70dd626347d52e07505e3704
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877535"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Diese Methode konvertiert entweder auf ein Objektspeicherort oder auf eine Speicheradresse, an einen Speicherkontext.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

#### <a name="parameters"></a>Parameter
 `pField`

 [in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , beschreibt das zu suchende Objekt. Wenn `NULL`, verwenden Sie dann `dwConstant` stattdessen.

 `dwConstant`

 [in] Eine Konstante Speicheradresse, z. B. 0x5000.

 `ppMemCxt`

 [out] Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle, die die Adresse des Objekts oder die Adresse im Speicher darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)