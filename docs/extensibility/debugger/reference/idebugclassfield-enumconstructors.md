---
title: IDebugClassField::EnumConstructors | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ecc2e2fba9dbddc12a58866c7edcde51b148af1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719101"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Erstellt einen Enumerator für die Konstruktoren für diese Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `cMatch`

 [in] Ein Wert aus der [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) -Enumeration, der den Typ der Konstruktoren verwenden, um die Enumeration angibt.

 `ppEnum`

 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Konstruktoren darstellt. Gibt einen null-Wert zurück, wenn es keine Konstruktoren gibt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn es keine Konstruktoren gibt. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jedes Element der Enumeration ist ein [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) Objekt, das eine Konstruktormethode beschreibt.

 Die Liste der Konstruktoren umfasst in der Regel nicht die Standardkonstruktoren, die vom Compiler bereitgestellt.

## <a name="see-also"></a>Siehe auch
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)