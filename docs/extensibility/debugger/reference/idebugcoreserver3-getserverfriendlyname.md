---
title: "IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs"
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
  - "IDebugCoreServer3::GetServerFriendlyName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen angezeigten Namen für den Server ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### Parameter  
 `pbstrName`  
 \[out\]  Gibt einen Anzeigenamen für den Server zurück.  
  
> [!NOTE]
>  Der Aufrufer ist für das Freigeben der Zeichenfolge verantwortlich.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Für USER\-gestartete Server ist der Name, der von dieser Methode zurückgegeben wird, der vollständige Name des Servers.  Für gestartete Server ist der Name des Computers, auf dem der Server ausgeführt wird.  
  
 Für einen maschinenorientierten Namen rufen Sie die [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)