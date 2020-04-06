---
title: IDebugArrayField::GetNumberOfElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 30318e1f17f93d1c9fc68bf5a4a9a0d4ae4cf353
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736318"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Ruft die Anzahl der Elemente im Array ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Parameter
`pdwNumElements`\
[out] Gibt die Anzahl der Elemente im Array zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der zurückgegebene Wert ist die Gesamtzahl der Elemente im Array, unabhängig von der Anzahl der Dimensionen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
