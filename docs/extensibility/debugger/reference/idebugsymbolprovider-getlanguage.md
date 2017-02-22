---
title: "IDebugSymbolProvider::GetLanguage | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetLanguage"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetLanguage-Methode"
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die Sprache ab, die verwendet wurde, um den Code an der Adresse Debuggen kompilieren.  
  
## Syntax  
  
```cpp#  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```c#  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Ein Adressen Objekt dargestellt durch eine [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle.  
  
 `pguidLanguage`  
 \[out\]  Gibt `GUID` zurück, der die Sprache angibt.  
  
 `pguidLanguageVendor`  
 \[out\]  Gibt `GUID` zurück, das den Compilerhersteller angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das Debugmodul ruft diese Methode auf, um die Informationen abzurufen, die den richtigen Ausdrucksauswertung auswählen muss.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)