---
title: "IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs"
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
  - "IDebugEnumField::GetValueFromStringCaseInsensitive"
helpviewer_keywords: 
  - "IDebugEnumField::GetValueFromStringCaseInsensitive-Methode"
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode verwendet eine Suche ohne Berücksichtigung der Groß\- und Kleinschreibung, um den Wert zurückzugeben, der dem Namen einer Enumerationskonstante zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### Parameter  
 `pszValue`  
 \[in\]  Eine Zeichenfolge, die den Namen angibt, für die der Wert abgerufen werden soll.  Beachten Sie, dass für C\+\+, dies ist eine Zeichenfolge mit Breitzeichen.  
  
 `pValue`  
 \[out\]  Gibt den zugeordneten numerischen Wert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE`, wenn der Name nicht Teil der Enumeration oder einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird die Groß\- und Kleinschreibung nicht berücksichtigt.  Wenn eine Suche unter Berücksichtigung der Groß\- und Kleinschreibung nicht erforderlich ist \(z. B. in einer Sprache wie C\+\+, an dem Namen die Groß\- und Kleinschreibung beachtet werden muss\), verwenden Sie [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)