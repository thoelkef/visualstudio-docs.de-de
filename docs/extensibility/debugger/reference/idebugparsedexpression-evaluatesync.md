---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "IDebugParsedExpression::EvaluateSync-Methode"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode wertet den analysierten Ausdruck aus und wandelt optional das Ergebnis in einen anderen Datentyp.  
  
## Syntax  
  
```cpp#  
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
  
```c#  
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
  
#### Parameter  
 `dwEvalFlags`  
 \[in\]  Eine Kombination von [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) Konstanten, die steuern, wie der Ausdruck ausgewertet werden soll.  
  
 `dwTimeout`  
 \[in\]  Bevor der Rückgabe dieser Methode gibt die maximale Zeit in Millisekunden an, zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
 `pSymbolProvider`  
 \[in\]  Der Anbieter Symbol als [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)\-Schnittstelle.  
  
 `pAddress`  
 \[in\]  Der aktuelle Position der Ausführung innerhalb einer Methode als [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle.  
  
 `pBinder`  
 \[in\]  Der Binder, ausgedrückt als [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)\-Schnittstelle.  
  
 `bstrResultType`  
 \[in\]  Der Typ des Ergebnisses umgewandelt werden soll.  Dieses Argument kann ein NULL\-Wert sein.  
  
 `ppResult`  
 \[out\]  Gibt die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle zurück, die die Ergebnisse der Auswertung darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Kontext ist Ausdrucksauswertungs von`pAddress`angegeben, der es ermöglicht, die enthaltende Methode bestimmen und die Sprache zu verwenden, macht die Regeln ausgewertet, um den Wert der Symbole im Ausdruck zu bestimmen.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)