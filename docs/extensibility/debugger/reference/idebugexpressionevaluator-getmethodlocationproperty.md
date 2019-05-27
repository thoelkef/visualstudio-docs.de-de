---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6770bfdd534069e70bb803334f87b382d57a6894
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200918"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Diese Methode konvertiert einen Methode Speicherort und einen Offset, in eine Speicheradresse.

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
[in] Der Speicherort der Methode und einem festen Offset, die als Zeichenfolge ausgedrückt werden.

`pSymbolProvider`\
[in] Der symbolanbieter, ausgedrückt als eine [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) Objekt.

`pAddress`\
[in] Eine Adresse innerhalb der Methode als eine [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt.

`pBinder`\
[in] Der Binder, ausgedrückt als eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Objekt.

`ppProperty`\
[out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle, die Speicheradresse darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die zurückgegebene Adresse kann verwendet werden, um einen Haltepunkt, z. B. festzulegen.

 Trotz des Namens `upstrFullyQualifiedMethodPlusOffset`, dieser Parameter kann einen Methodennamen teilweise gekennzeichnete übergeben werden. In diesem Fall wird die ausgewählte Methode, die eingeschlossen `pAddress`. Der Interpretation dieser Parameter ist der Implementierung von der ausdrucksauswertung und die unterstützte Sprache an.

## <a name="see-also"></a>Siehe auch
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)