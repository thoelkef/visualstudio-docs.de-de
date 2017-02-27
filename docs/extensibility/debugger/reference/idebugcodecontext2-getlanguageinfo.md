---
title: "IDebugCodeContext2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Sprachinformationen für diesen Code Elementkontext ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### Parameter  
 `pbstrLanguage`  
 \[in, out\]  Gibt eine Zeichenfolge mit dem Namen der Programmiersprache enthält, z. B. „C\+\+“ zurück.  
  
 `pguidLanguage`  
 \[in, out\]  Gibt die GUID für die Sprache des Codes kontexts z. B. `guidCPPLang`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Mindestens einer der Parameter muss einen Wert ungleich null zurückgegeben.  
  
## Siehe auch  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)