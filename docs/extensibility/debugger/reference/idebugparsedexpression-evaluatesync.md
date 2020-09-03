---
title: 'Idebugparser-dexpression:: evaluatesync | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726010"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Diese Methode wertet den analysierten Ausdruck aus und wandelt das Ergebnis optional in einen anderen Datentyp um.

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
in Eine Kombination aus [evalflags](../../../extensibility/debugger/reference/evalflags.md) -Konstanten, die Steuern, wie der Ausdruck ausgewertet werden soll.

`dwTimeout`\
in Gibt die maximale Zeit in Millisekunden an, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.

`pSymbolProvider`\
in Der Symbol Anbieter, ausgedrückt als [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Schnittstelle.

`pAddress`\
in Der aktuelle Ausführungs Speicherort innerhalb einer Methode, ausgedrückt als [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle.

`pBinder`\
in Der Binder, ausgedrückt als [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle.

`bstrResultType`\
in Der Typ, in den das Ergebnis umgewandelt werden soll. Dieses Argument kann ein NULL-Wert sein.

`ppResult`\
vorgenommen Gibt die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurück, die die Ergebnisse der Auswertung darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Ausdrucks Auswertungs Kontext wird durch angegeben `pAddress` , wodurch es möglich ist, die enthaltende Methode zu bestimmen und dann die sprach Bereichs Regeln zu verwenden, um den Wert der Symbole im Ausdruck zu ermitteln.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
