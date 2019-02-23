---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c2fc6b9b7683180c3a9c3f2aa967ba171a48097
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690681"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Erstellt eine Feldinstanz, die ein Array von Typargumenten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

#### <a name="parameters"></a>Parameter
 `cArgs`

 [in] Anzahl der Argumente in der `ppArgs` Array.

 `ppArgs`

 [in] Ein Array, das die Typargumente enthält. Die Typargumente müssen es sich um geschlossene Typen (Generika nicht generisch oder vollständig instanziiert) sein.

 `ppConstructedField`

 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die das neue Feld darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Einschränkungen werden nicht überprüft.

## <a name="see-also"></a>Siehe auch
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)