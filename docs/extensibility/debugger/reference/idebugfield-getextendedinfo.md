---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728876"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Diese Methode erhält erweiterte Informationen zu einem Feld.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parameter
`guidExtendedInfo`\
[in] Wählt die zurückzugebenden Informationen aus. Gültige Werte sind:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`guidConstantValue`|Der Wert als eine Sequenz von Bytes.|
|`guidConstantType`|Der Typ als Typsignatur.|

`prgBuffer`\
[out] Gibt die erweiterten Informationen zurück.

`pdwLen`\
[in, out] Gibt die Größe der erweiterten Informationen in Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Derzeit gibt diese Methode nur den Typ oder Wert einer Konstante zurück. Der Aufrufer muss den `prgBuffer` zurückgegebenen Puffer `CoTaskMemFree` durch Aufrufen der COM-Funktion (C++) oder <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C- freizugeben).

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
