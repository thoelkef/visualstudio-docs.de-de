---
title: "IDebugExpressionContext2::ParseText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2::ParseText"
helpviewer_keywords: 
  - "IDebugExpressionContext2::ParseText"
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2::ParseText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Analysiert einen Ausdruck in Form der Text für spätere Auswertung.  
  
## Syntax  
  
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
  
```c#  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### Parameter  
 `pszCode`  
 \[in\]  Der zu analysierende Ausdruck.  
  
 `dwFlags`  
 \[in\]  Eine Kombination von Flags aus der [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)\-Enumeration, die die Analyse steuert.  
  
 `nRadix`  
 \[in\]  Die Basis verwendet werden soll, wenn alle numerischen Daten in `pszCode`analysiert werden.  
  
 `ppExpr`  
 \[out\]  Gibt das [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)\-Objekt zurück, das den analysierten Ausdruck darstellt, der zum Binden und zur Auswertung bereit ist.  
  
 `pbstrError`  
 \[out\]  Gibt die Fehlermeldung zurück, wenn der Ausdruck einen Fehler enthält.  
  
 `pichError`  
 \[out\]  Gibt den Zeichenindex des Fehlers in `pszCode` zurück, wenn der Ausdruck einen Fehler enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn diese Methode aufgerufen wird, sollte eine Debug\- Modul \(DE\) den Ausdruck analysieren und ihn für die ordnungsgemäße Ausführung überprüfen.  Die `pbstrError` und `pichError`\-Parameter ausgefüllt werden kann, wenn der Ausdruck ungültig ist.  
  
 Beachten Sie, dass der Ausdruck nicht ausgewertet wird, werden nur analysiert.  Neuere Aufruf der [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)\-Methode wertet den analysierten Ausdruck aus.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CEnvBlock`\-Objekt implementiert, das die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle verfügbar macht.  Dieses Beispiel liest den Ausdruck als analysiert als Name einer Umgebungsvariablen und ruft den Wert dieser Variablen ab.  
  
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
  
## Siehe auch  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)