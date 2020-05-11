---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726244"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ruft das Feld oder die Variable (falls vorhanden) ab, die die eigenschaft, die durch dieses Objekt dargestellt wird, unterstützen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parameter
`ppObject`\
[out] Ein [IDebugObject2-Objekt,](../../../extensibility/debugger/reference/idebugobject2.md) das das Sicherungsfeld beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Das [IDebugObject2-Objekt](../../../extensibility/debugger/reference/idebugobject2.md) stellt eine verwaltete Codeklasseneigenschaft dar, d. h. eine Methode mit einem get- und/oder set-Accessor. Solche Eigenschaften erfordern im Allgemeinen, dass eine Variable den von der Eigenschaft bearbeiteten Wert enthält. Diese Variable wird als Sicherungsfeld bezeichnet. Wenn kein Sicherungsfeld für das Objekt vorhanden ist, stellen Sie sicher, dass Sie einen NULL-Wert zurückgeben: Einige Aufrufer achten `ppObject`möglicherweise nicht auf den Rückgabewert, sondern suchen stattdessen, ob ein NULL-Wert in zurückgegeben wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
