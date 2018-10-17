---
title: IDebugExpressionContext2::ParseText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 707c8dd7d6e690c621c9c6c00db61be8dc291095
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214954"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Analysiert einen Ausdruck im Text-Format für die spätere Auswertung an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in] Der Ausdruck analysiert werden.  
  
 `dwFlags`  
 [in] Eine Kombination von Flags aus der [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) -Enumeration, der steuert, analysieren.  
  
 `nRadix`  
 [in] Die Basis verwendet werden, bei der Analyse keine numerische Informationen im `pszCode`.  
  
 `ppExpr`  
 [out] Gibt die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) -Objekt, das den analysierten Ausdruck darstellt, die für die Bindung und die Auswertung kann.  
  
 `pbstrError`  
 [out] Gibt die Fehlermeldung zurück, wenn der Ausdruck einen Fehler enthält.  
  
 `pichError`  
 [out] Gibt den Zeichenindex des Fehlers im `pszCode` , wenn der Ausdruck einen Fehler enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode aufgerufen wird, sollte eine Debug-Engine (DE) Analysieren des Ausdrucks und auf Richtigkeit zu überprüfen. Die `pbstrError` und `pichError` Parameter möglicherweise ausgefüllt, wenn der Ausdruck ungültig ist.  
  
 Beachten Sie, dass der Ausdruck nicht ausgewertet wird, nur analysiert. Ein späterer Aufruf von der [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methoden wertet den analysierten Ausdruck.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CEnvBlock` -Objekt, das macht die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Dieses Beispiel berücksichtigt den Ausdruck, der als Name einer Umgebungsvariable analysiert werden und ruft den Wert dieser Variable ab.  
  
```cpp#  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

