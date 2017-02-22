---
title: "IDebugEnumField::GetValueFromString | Microsoft Docs"
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
  - "IDebugEnumField::GetValueFromString"
helpviewer_keywords: 
  - "IDebugEnumField::GetValueFromString-Methode"
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt den Wert zurück, der dem Namen einer Enumerationskonstante zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromString(  
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
 Bei dieser Methode wird die Groß\- und Kleinschreibung berücksichtigt.  Wenn eine Suche ohne Berücksichtigung der Groß\- und Kleinschreibung nicht erforderlich ist \(z. B. in einer Sprache wie Visual Basic, in dem keine Namen die Groß\- und Kleinschreibung berücksichtigt wird\), verwenden Sie [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)