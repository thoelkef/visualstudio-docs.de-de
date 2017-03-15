---
title: "IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromPosition"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromPosition-Methode"
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ordnet eine Position des Dokuments in ein Array von Adressen zu debuggen.  
  
## Syntax  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### Parameter  
 `pDocPos`  
 \[in\]  Die Position des Dokuments.  
  
 `fStatmentOnly`  
 \[in\]  Wenn TRUE, Begrenzungen die Programmdebuginformationen Adressen zu einer einzelnen Anweisung.  
  
 `ppEnumBegAddresses`  
 \[out\]  Gibt einen Enumerator zum Debuggen starten die Adressen zurück, die mit dieser Anweisung oder Zeile zugeordnet werden.  
  
 `ppEnumEndAddresses`  
 \[out\]  Gibt einen [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) Enumerator für die Debug\- Adressen des Endes zurück, die mit dieser Anweisung oder Zeile zugeordnet werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Eine Position des Dokuments gibt in der Regel einen Bereich von Quellzeilen an.  Diese Methode stellt die Anfangs\- und EndAdressen Debuggen, die mit diesen Zeilen zugeordnet sind.  Einige Sprachen ermöglichen Anweisungen, die mehrere Zeilen umfassen, oder Zeilen, die mehr als eine Anweisung enthält.  Diese Methode stellt ein Flag, um die Programmdebuginformationen Adressen zu einer einzigen Anweisung zu beschränken.  
  
 Es ist möglich, Debugsymbolinformationen für eine einzelne Anweisung mehrere Adressen, wie im Fall von Vorlagen zu haben.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)