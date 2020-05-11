---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734473"
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

## <a name="parameters"></a>Parameter
`ppEnum`\

[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der Basisklassen darstellt. Gibt einen NULL-Wert zurück, wenn keine Basisklassen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK zurück, gibt S_SH_NO_BASE_CLASSES zurück, wenn keine Basisklassen vorhanden sind (und der `ppEnum` Parameter auf einen NULL-Wert festgelegt ist); Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Basisklassen im Enumeratorobjekt werden in der Reihenfolge der unmittelbarsten (oder am meisten abgeleiteten) Basisklasse für die entferntesten Basisklasse angegeben. Beispielsweise, wenn die C++-Klassen angegeben werden:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Die Enumeration gibt die Basisklassen `Level2` `Level1`in `Root`der Reihenfolge zurück , .

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
