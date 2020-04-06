---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729522"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Diese Methode konvertiert eine Methodenposition und versatz in eine Speicheradresse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parameter
`upstrFullyQualifiedMethodPlusOffset`\
[in] Die Methodenposition und der Offset, ausgedrückt als Zeichenfolge.

`pSymbolProvider`\
[in] Der Symbolanbieter, der als [IDebugSymbolProvider-Objekt](../../../extensibility/debugger/reference/idebugsymbolprovider.md) ausgedrückt wird.

`pAddress`\
[in] Eine Adresse innerhalb der Methode, ausgedrückt als [IDebugAddress-Objekt.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[in] Der Binder wird als [IDebugBinder-Objekt](../../../extensibility/debugger/reference/idebugbinder.md) ausgedrückt.

`ppProperty`\
[out] Gibt eine [IDebugProperty2-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, die die Speicheradresse darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die zurückgegebene Adresse kann z. B. zum Festlegen eines Haltepunkts verwendet werden.

 Trotz des `upstrFullyQualifiedMethodPlusOffset`Namens kann dieser Parameter an einen teilweise qualifizierten Methodennamen übergeben werden. In diesem Fall ist die ausgewählte Methode `pAddress`diejenige, die umschließt. Wie dieser Parameter interpretiert wird, hängt von der Implementierung des Ausdrucksevaluators und der unterstützten Sprache ab.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
