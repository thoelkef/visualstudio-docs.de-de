---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726010"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Diese Methode wertet den analysierten Ausdruck aus und übergibt das Ergebnis optional in einen anderen Datentyp.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parameter
`dwEvalFlags`\
[in] Eine Kombination von [EVALFLAGS-Konstanten,](../../../extensibility/debugger/reference/evalflags.md) die steuern, wie der Ausdruck ausgewertet werden soll.

`dwTimeout`\
[in] Gibt die maximale Wartezeit in Millisekunden an, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`pSymbolProvider`\
[in] Der Symbolanbieter, ausgedrückt als [IDebugSymbolProvider-Schnittstelle.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[in] Der aktuelle Ausführungsspeicherort innerhalb einer Methode, ausgedrückt als [IDebugAddress-Schnittstelle.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[in] Der Binder, ausgedrückt als [IDebugBinder-Schnittstelle.](../../../extensibility/debugger/reference/idebugbinder.md)

`bstrResultType`\
[in] Der Typ, auf den das Ergebnis umgegossen werden soll. Dieses Argument kann ein NULL-Wert sein.

`ppResult`\
[out] Gibt die [IDebugProperty2-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, die die Auswertungsergebnisse darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Ausdrucksauswertungskontext `pAddress`wird durch angegeben, wodurch es möglich ist, die enthaltende Methode zu bestimmen und dann Sprachbereichsregeln zu verwenden, um den Wert der Symbole im Ausdruck zu bestimmen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
