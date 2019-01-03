---
title: IDebugExpressionEvaluator3::Parse2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2236276e5d97b8c0d3d38921206ffd7d9506e243
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901700"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck erhält der symbolanbieter und die Adresse des Frames, ausgewertet.  
  
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
  
#### <a name="parameters"></a>Parameter  
 `upstrExpression`  
 [in] Die Ausdruckszeichenfolge analysiert werden.  
  
 `dwFlags`  
 [in] Eine Auflistung von [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Konstanten, die bestimmen, wie der Ausdruck ist, die analysiert werden.  
  
 `nRadix`  
 [in] Die Basis, die verwendet werden, um alle numerischen Informationen interpretieren.  
  
 `pSymbolProvider`  
 [in] Schnittstelle, die von der symbolanbieter.  
  
 `pAddress`  
 [in] Die Adresse des Frames, ausgewertet.  
  
 `pbstrError`  
 [out] Gibt den Fehler als Klartext zurück.  
  
 `pichError`  
 [out] Gibt die Zeichenposition des Starts des Fehlers in der Ausdruckszeichenfolge zurück.  
  
 `ppParsedExpression`  
 [out] Gibt den analysierten Ausdruck in einem [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erzeugt einen analysierten Ausdruck, der nicht auf einen tatsächlichen Wert. Ein analysierten Ausdruck kann ausgewertet werden, d. h. in einen Wert konvertiert.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CEE** -Objekt, das macht die [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) Schnittstelle.  
  
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
        out_pbstrError      ,   // BSTR*  
        inout_pichError,        // UINT*  
        pSymbolProvider,  
        out_ppParsedExpression  // Output  
    };  
  
    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)