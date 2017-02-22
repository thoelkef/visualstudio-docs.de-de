---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
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
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "IDebugModule2::ReloadSymbols-Methode"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

VERALTET.  NOT TUN USE.  Lädt die Symbole für dieses Modul.  
  
## Syntax  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### Parameter  
 `pszUrlToSymbols`  
 \[in\]  Der Pfad des Symbolspeichers.  
  
 `pbstrDebugMessage`  
 \[out\]  Gibt eine Informationsmeldung, z. B. einen Status oder eine Fehlermeldung zurück, die rechts neben dem Namen des Moduls im Fenster Module angezeigt werden sollen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Ein Modul sollte immer `E_FAIL`Debug zurückgeben.  
  
## Hinweise  
 Diese Methode wird nicht mehr unterstützt.  Implementieren Sie die [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)\-Methode.  
  
## Siehe auch  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)