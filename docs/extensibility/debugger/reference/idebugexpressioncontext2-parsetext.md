---
title: IDebugExpressionContext2::ParseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8494c9c90c4cb6e94115c542a25e12e948f7064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729650"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analysiert einen Ausdruck in Textform für eine spätere Auswertung.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Parameter
`pszCode`\
[in] Der zu analysierende Ausdruck.

`dwFlags`\
[in] Eine Kombination von Flags aus der PARSEFLAGS-Enumeration, die die Analyse steuert. [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)

`nRadix`\
[in] Der Radix, der zum Analysieren numerischer Informationen in `pszCode`verwendet werden soll.

`ppExpr`\
[out] Gibt das [IDebugExpression2-Objekt](../../../extensibility/debugger/reference/idebugexpression2.md) zurück, das den analysierten Ausdruck darstellt, der für die Bindung und Auswertung bereit ist.

`pbstrError`\
[out] Gibt die Fehlermeldung zurück, wenn der Ausdruck einen Fehler enthält.

`pichError`\
[out] Gibt den Zeichenindex des `pszCode` Fehlers in zurück, wenn der Ausdruck einen Fehler enthält.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Wenn diese Methode aufgerufen wird, sollte ein Debugmodul (DE) den Ausdruck analysieren und auf Korrektheit überprüfen. Die `pbstrError` `pichError` und Parameter können ausgefüllt werden, wenn der Ausdruck ungültig ist.

Beachten Sie, dass der Ausdruck nicht ausgewertet, sondern nur analysiert wird. Ein späterer Aufruf der [EvaluateSync-](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync-Methoden](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) wertet den analysierten Ausdruck aus.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CEnvBlock` Methode für ein einfaches Objekt implementiert wird, das die [IDebugExpressionContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) verfügbar macht. In diesem Beispiel wird der Ausdruck als Name einer Umgebungsvariablen analysiert und der Wert aus dieser Variablen abgerufen.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
