---
title: "IDebugExpressionEvaluator3::Parse2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator3::Parse2"
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator3::Parse2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Konvertiert eine Ausdruckszeichenfolge in ein analysierten angegebenen Ausdruck der Symbol und die Adresse der auswertenden Frames.  
  
## Syntax  
  
```cpp#  
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
  
```c#  
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
  
#### Parameter  
 `upstrExpression`  
 \[in\]  Die zu analysierende Ausdruckszeichenfolge.  
  
 `dwFlags`  
 \[in\]  Eine Auflistung [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Konstanten, die bestimmen, wie der Ausdruck analysiert werden soll.  
  
 `nRadix`  
 \[in\]  Informationen zum Interpretieren eines numerischen Basis verwendet werden soll.  
  
 `pSymbolProvider`  
 \[in\]  Symbol Schnittstelle des Anbieters.  
  
 `pAddress`  
 \[in\]  Adresse der auswertenden Frames.  
  
 `pbstrError`  
 \[out\]  Gibt den Fehler als Nur\-Text zurück.  
  
 `pichError`  
 \[out\]  Gibt die Zeichenposition des Anfangs des Fehlers in der Ausdruckszeichenfolge zurück.  
  
 `ppParsedExpression`  
 \[out\]  Gibt den analysierten Ausdruck in einem [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode erzeugt einen analysierten Ausdruck keinen Wert.  Ein analysierter Ausdruck kann jetzt ausgewertet werden, d. h. in einen Wert konvertiert.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CEE**\-Objekt implementiert, das die [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
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
  
## Siehe auch  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)