---
title: "IDebugSymbolProvider::GetNextAddress | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetNextAddress"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetNextAddress-Methode"
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetNextAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Adresse ab, die die ein angegebenes debuggen Adresse in einer Methode erfolgreich ausgeführt wurde.  
  
## Syntax  
  
```cpp#  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```c#  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Bei Debug Adresse.  
  
 `fStatementOnly`  
 \[in\]  Wenn TRUE, Begrenzungen die Programmdebuginformationen Adressen zu einer einzelnen Anweisung.  
  
 `ppAddress`  
 \[out\]  Gibt das nächste debuggen Adresse zurück.  
  
## Rückgabewert  
 Gibt eine gültige `HRESULT`, normalerweise S\_OK zurück.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)