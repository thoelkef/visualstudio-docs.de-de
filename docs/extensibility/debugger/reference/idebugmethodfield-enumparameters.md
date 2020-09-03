---
title: 'Idebugmethodfield:: EnumParameters | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
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
vorgenommen Gibt ein [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Parameter für die Methode darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, wenn keine Parameter vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben oder S_FALSE zurückgegeben, wenn keine Parameter vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element ist ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das verschiedene Typen von Parametern darstellt. Aufrufen der [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode für jedes Objekt, um genau zu bestimmen, welche Art von Parameter das Objekt darstellt.

 Ein Parameter enthält sowohl den Variablennamen als auch seinen Typ. Der erste Parameter einer Klassenmethode ist in der Regel der "This"-Zeiger.

 Wenn nur die Typen der Parameter benötigt werden, müssen Sie die [enumarguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) -Methode aufzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
