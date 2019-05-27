---
title: IDebugPortPicker::DisplayPortPicker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00923556927f2fed7e5895df2db391a45463e57e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212904"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Zeigt das angegebene Dialogfeld an, das dem Benutzer ermöglicht, einen Port auszuwählen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parameter
`hwndParentDialog`\
[in] Handle für das übergeordnete Dialogfeld.

`pbstrPortId`\
[out] Port-ID-Zeichenfolge.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Der Rückgabewert `S_FALSE` (oder einen Rückgabewert von `S_OK` mit der `BSTR` festgelegt `NULL`) gibt an, dass der Benutzer geklickt hat **Abbrechen**.

## <a name="see-also"></a>Siehe auch
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)