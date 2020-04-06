---
title: IDebugCustomAttribute::GetparentField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fae84a4d02438335aea00c50dd9b89520d08bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732700"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Ruft das Feld ab, dem das benutzerdefinierte Attribut zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
[out] Gibt das [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) zurück, das das Feld darstellt, dem das benutzerdefinierte Attribut zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie die [GetKind-Methode](../../../extensibility/debugger/reference/idebugfield-getkind.md) für das zurückgegebene [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) auf, um zu bestimmen, um welche Art von Feld das übergeordnete Feld ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
