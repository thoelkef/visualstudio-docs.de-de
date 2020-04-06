---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724890"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Zeigt das angegebene Dialogfeld an, in dem der Benutzer einen Port auswählen kann.

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
[out] Port-Bezeichnerzeichenfolge.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Ein Rückgabewert `S_FALSE` von (oder `S_OK` ein `BSTR` Rückgabewert `NULL`von mit dem Satz auf ) gibt an, dass der Benutzer auf **Abbrechen**geklickt hat.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
