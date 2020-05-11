---
title: IDebugExpressionEvaluator3::Parse2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5254d30ed1a656bfd357fca822efa554d895807e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729125"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck, der den Symbolanbieter und die Adresse des auswertenden Frames angibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Parse2 (
    LPCOLESTR                upstrExpression,
    PARSEFLAGS               dwFlags,
    UINT                     nRadix,
    IDebugSymbolProvider*    pSymbolProvider,
    IDebugAddress*           pAddress,
    BSTR*                    pbstrError,
    UINT*                    pichError,
    IDebugParsedExpression** ppParsedExpression
);
```

```csharp
HRESULT Parse2 (
    string                     upstrExpression,
    enum_PARSEFLAGS            dwFlags,
    uint                       nRadix,
    IDebugSymbolProvider       pSymbolProvider,
    IDebugAddress              pAddress,
    out string                 pbstrError,
    out uint                   pichError,
    out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parameter
`upstrExpression`\
[in] Die zu analysierende Ausdruckszeichenfolge.

`dwFlags`\
[in] Eine Auflistung von [PARSEFLAGS-Konstanten,](../../../extensibility/debugger/reference/parseflags.md) die bestimmen, wie der Ausdruck analysiert werden soll.

`nRadix`\
[in] Radix zur Interpretation numerischer Informationen.

`pSymbolProvider`\
[in] Schnittstelle des Symbolanbieters.

`pAddress`\
[in] Adresse des Auswerterahmens.

`pbstrError`\
[out] Gibt den Fehler als lesbaren Text zurück.

`pichError`\
[out] Gibt die Zeichenposition des Anfangs des Fehlers in der Ausdruckszeichenfolge zurück.

`ppParsedExpression`\
[out] Gibt den analysierten Ausdruck in einem [IDebugParsedExpression-Objekt](../../../extensibility/debugger/reference/idebugparsedexpression.md) zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Diese Methode erzeugt einen analysierten Ausdruck und keinen tatsächlichen Wert. Ein analysierter Ausdruck kann ausgewertet werden, d. h. in einen Wert konvertiert werden.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CEE-Objekt** implementiert wird, das die [IDebugExpressionEvaluator3-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) verfügbar macht.

```cpp
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,
  PARSEFLAGS in_FLAGS,
  UINT in_RADIX,
  IDebugSymbolProvider *pSymbolProvider,
  IDebugAddress *pAddress,
  BSTR* out_pbstrError,
  UINT* inout_pichError,
  IDebugParsedExpression** out_ppParsedExpression )
{
    // precondition
    REQUIRE( NULL != in_szExprText );
    //REQUIRE( NULL != out_pbstrError );
    REQUIRE( NULL != inout_pichError );
    REQUIRE( NULL != out_ppParsedExpression );

    if (NULL == in_szExprText)
        return E_INVALIDARG;

    if (NULL == inout_pichError)
        return E_POINTER;

    if (NULL == out_ppParsedExpression)
        return E_POINTER;

    if (out_pbstrError)
        *out_pbstrError = NULL;

    *out_ppParsedExpression = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    // function body
    EEDomain::fParseExpression DomainVal =
    {
        this,                   // CEE*
        in_szExprText,          // LPCOLESTR
        in_FLAGS,               // EVALFLAGS
        in_RADIX,               // RADIX
        out_pbstrError,         // BSTR*
        inout_pichError,        // UINT*
        pSymbolProvider,
        out_ppParsedExpression  // Output
    };

    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
