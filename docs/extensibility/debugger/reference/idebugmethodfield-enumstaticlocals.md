---
title: IDebugMethodField::EnumStaticLocals | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 006f1975c18aa7464531654d9b71fd857953afc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324241"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Erstellt einen Enumerator für statische lokale Variablen der Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parameter
`ppLocals`\
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der statischen lokalen Variablen darstellt. Gibt einen null-Wert zurück, wenn keine statische lokale Variablen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn keine statische lokale Variablen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das verschiedene Arten von statischen lokalen Variablen darstellt. Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Methode für jedes Objekt, um zu bestimmen, genau welche Art von statischen lokalen das-Objekt darstellt.

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)