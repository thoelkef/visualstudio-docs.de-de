---
title: IDebugProperty2::SetValueasString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721239"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Legt den Wert einer Eigenschaft aus einer bestimmten Zeichenfolge fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parameter
`pszValue`\
[in] Eine Zeichenfolge, die den festzulegenden Wert enthält.

`nRadix`\
[in] Ein Radix, der bei der Interpretation numerischer Informationen verwendet werden soll. Dies kann 0 sein, um zu versuchen, den Radix automatisch zu bestimmen.

`dwTimeout`\
[in] Gibt die maximale Wartezeit in Millisekunden an, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben. Die folgende Tabelle zeigt andere mögliche Werte.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Die Zeichenfolge konnte nicht in einen Eigenschaftswert konvertiert werden, oder der Eigenschaftswert konnte nicht festgelegt werden.|
|`E_SETVALUE_VALUE_IS_READONLY`|Die Eigenschaft ist schreibgeschützt.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
