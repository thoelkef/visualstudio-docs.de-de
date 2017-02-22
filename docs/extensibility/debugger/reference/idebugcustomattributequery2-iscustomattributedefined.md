---
title: "IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::IsCustomAttributeDefined"
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob sich ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.  
  
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
 Gibt S\_OK, wenn das benutzerdefinierte Attribut für dieses Feld definierten zurückgibt, andernfalls S\_FALSE zurück.  
  
## Hinweise  
 Um die Attributdaten abgerufen, die mit dem benutzerdefinierten Attribut zugeordnet sind, rufen Sie die [\[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)