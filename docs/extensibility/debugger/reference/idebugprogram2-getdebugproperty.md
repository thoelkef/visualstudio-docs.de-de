---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722895"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Ruft die Eigenschaften des Programms ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parameter
`ppProperty`\
[out] Gibt ein [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, das die Eigenschaften des Programms darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die von dieser Methode zurückgegebenen Eigenschaften sind programmspezifisch. Wenn das Programm mehr als eine Eigenschaft zurückgeben muss, ist das von dieser Methode [zurückgegebene IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) ein Container mit zusätzlichen Eigenschaften, und das Aufrufen der [EnumChildren-Methode](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) gibt eine Liste aller Eigenschaften zurück.

 Ein Programm kann eine beliebige Anzahl und Art zusätzlicher `IDebugProperty2` Eigenschaften verfügbar machen, die über die Schnittstelle beschrieben werden können. Eine IDE kann die zusätzlichen Programmeigenschaften über eine generische Eigenschaftenbrowser-Benutzeroberfläche anzeigen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
