---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729504"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Diese Methode ruft ein Eigenschaftsobjekt ab, das die Locals, Argumente und andere Eigenschaften einer Methode enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parameter
`pSymbolProvider`\
[in] Der zu verwendende Symbolanbieter, ausgedrückt als [IDebugSymbolProvider-Objekt.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[in] Die Adresse im Code, ausgedrückt als [IDebugAddress-Objekt,](../../../extensibility/debugger/reference/idebugaddress.md) die in die nächste enthaltende Funktion aufgelöst werden soll.

`pBinder`\
[in] Der zu verwendende Binder, ausgedrückt als [IDebugBinder-Objekt.](../../../extensibility/debugger/reference/idebugbinder.md)

`fIncludeHiddenLocals`\
[in] Ungleich`TRUE`Null ( )bedeutet, versteckte Locals einzubeziehen; Null`FALSE`( ) bedeutet, versteckte Einheimische wegzulassen

`ppProperty`\
[out] Gibt ein [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, das die Methode darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ausgeblendete Locals sind in der Regel Variablen, die vom Compiler generiert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
