---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext-Methode"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ordnet den Dokumentenkontext in ein Array von Adressen zu.  
  
## Syntax  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### Parameter  
 `pDocContext`  
 \[in\]  Der Dokumentenkontext.  
  
 `fStatmentOnly`  
 \[in\]  Wenn TRUE, Begrenzungen die Programmdebuginformationen Adressen zu einer einzelnen Anweisung.  
  
 `ppEnumBegAddresses`  
 \[out\]  Gibt einen Enumerator zum Debuggen starten die Adressen zurück, die mit dieser Anweisung oder Zeile zugeordnet werden.  
  
 `ppEnumEndAddresses`  
 \[out\]  Gibt einen [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) Enumerator für die Debug\- Adressen des Endes zurück, die mit dieser Anweisung oder Zeile zugeordnet werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Dokumentenkontext gibt in der Regel einen Bereich von Quellzeilen an.  Diese Methode stellt die Anfangs\- und EndAdressen Debuggen, die mit diesen Zeilen zugeordnet sind.  Einige Sprachen ermöglichen Anweisungen, die mehrere Zeilen umfassen, oder Zeilen, die mehr als eine Anweisung enthält.  Diese Methode stellt ein Flag, um die Programmdebuginformationen Adressen zu einer einzigen Anweisung zu beschränken.  
  
 Es ist möglich, Debugsymbolinformationen für eine einzelne Anweisung mehrere Adressen, wie im Fall von Vorlagen zu haben.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)