---
title: IDebugClassField::EnumBaseClasses | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74889ed04dceb133c80467d20f723f9561b6e25c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922764"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Erstellt einen Enumerator für die Basisklassen dieser Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `ppEnum`

 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Basisklassen darstellt. Gibt einen null-Wert zurück, wenn keine Basisklassen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, gibt S_SH_NO_BASE_CLASSES zurück, wenn keine Basisklassen vorhanden sind (und die `ppEnum` -Parameter auf einen null-Wert festgelegt ist), andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Basisklassen im Enumerator-Objekt werden in der Reihenfolge der Basisklasse am unmittelbarsten (oder am stärksten abgeleiteten) auf die meisten RAS Basisklasse angegeben. Angenommen, die C++-Klassen:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Die Basisklassen in der Reihenfolge die Enumeration zurück `Level2`, `Level1`, `Root`.

## <a name="see-also"></a>Siehe auch
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)