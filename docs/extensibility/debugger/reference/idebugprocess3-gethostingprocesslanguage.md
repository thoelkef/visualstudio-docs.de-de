---
title: "IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs"
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
  - "IDebugProcess3::GetHostingProcessLanguage"
helpviewer_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::GetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt `GUID` zurück, der die Sprache darstellt wie dieses Prozesses, legen Sie durch einen Aufruf von [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).  
  
## Syntax  
  
```cpp  
HRESULT GetHostingProcessLanguage(  
   GUID* pguidLang  
);  
```  
  
```c#  
int GetHostingProcessLanguage(  
   out Guid pguidLang  
);  
```  
  
#### Parameter  
 `pguidLang`  
 \[out\]  `GUID` der Sprache des Prozesses.  `GUID_NULL` \(C\+\+\) oder `Guid.Empty` \(C\#\) bedeutet, dass die Sprache nicht festgelegt ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)