---
title: "IDebugProgramHost2::GetHostName | Microsoft Docs"
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
  - "IDebugProgramHost2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostName"
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Titel des Anzeigenamens, oder der Dateiname des Prozesses Hosten des Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### Parameter  
 `dwType`  
 \[in\]  Ein Wert aus der [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)\-Enumeration.  
  
 `pbstrHostName`  
 \[out\]  Gibt den angeforderten Namen des Hosting Prozesses zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 In einer typischen Implementierung dieser Methode wird der `dwType`\-Parameter ignoriert und ein Anzeigename des Host computers wird zurückgegeben.  Eine weitere mögliche Implementierung besteht darin, den `dwType`\-Parameter in einem Aufruf der [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)\-Methode übergeben, um den Namen abzurufen.  
  
## Siehe auch  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)