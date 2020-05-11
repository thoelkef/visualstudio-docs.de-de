---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727200"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Erstellt einen Enumerator für die Parameter der Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der Parameter für die Methode darstellt. Andernfalls gibt ein NULL-Wert zurück, wenn keine Parameter vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine Parameter vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element ist ein [IDebugField-Objekt,](../../../extensibility/debugger/reference/idebugfield.md) das verschiedene Parametertypen darstellt. Rufen Sie die [GetKind-Methode](../../../extensibility/debugger/reference/idebugfield-getkind.md) für jedes Objekt auf, um genau zu bestimmen, welche Art von Parameter das Objekt darstellt.

 Ein Parameter enthält sowohl den Variablennamen als auch seinen Typ. Der erste Parameter für eine Klassenmethode ist in der Regel der "this"-Zeiger.

 Wenn nur die Typen der Parameter benötigt werden, rufen Sie die [EnumArguments-Methode](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
