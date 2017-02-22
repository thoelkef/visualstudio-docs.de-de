---
title: "IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs"
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
  - "IDebugMethodField::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "IDebugMethodField::IsCustomAttributeDefined-Methode"
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.  
  
## Syntax  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```c#  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### Parameter  
 `pszCustomAttributeName`  
 \[in\]  Eine Zeichenfolge, die den Namen des benutzerdefinierten Attributs, das gesucht werden soll.  
  
## Rückgabewert  
 Gibt S\_OK, wenn das benutzerdefinierte Attribut für diese Methode definiert ist, andernfalls gibt S\_FALSE zurück.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)