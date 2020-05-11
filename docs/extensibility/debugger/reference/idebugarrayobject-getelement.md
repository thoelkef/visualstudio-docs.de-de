---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736183"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Ruft ein Element des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parameter
`dwIndex`\
[in] Der Elementindex.

`ppElement`\
[out] Gibt eine [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) zurück, die das Element darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode sieht alle Elemente eines Arrayobjekts als eindimensionales Array, auch wenn das Arrayobjekt mehrdimensional ist. Wenn sie z. `myarray[3][2][6]` B. das Array und `dwIndex` den Parameter `myarray[1][1][2]`20 `dwIndex` angeben, würde diese Methode `myarray[1][1][3]`das Element von zurückgeben, und ein Parameter von 21 würde das Element von zurückgeben. Verwenden Sie die [GetCount-Methode,](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) um die Gesamtzahl der Elemente im Array zu bestimmen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
