---
title: "IDebugProgramNode2::GetEngineInfo | Microsoft Docs"
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
  - "IDebugProgramNode2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen und den Bezeichner des Debugmoduls \(DE\) Ausführung eines Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### Parameter  
 `pbstrEngine`  
 \[out\]  Gibt den Namen DEs running das Programm zurück \(C\+\+\-specific: Dieser kann ein NULL\-Zeiger sein, der angibt, dass der Aufrufer nicht im Namen des Moduls interessiert ist\).  
  
 `pguidEngine`  
 \[out\]  Gibt den Globally Unique Identifier DEs running das Programm zurück \(C\+\+\-specific: Dieser kann ein NULL\-Zeiger sein, der angibt, dass der Aufrufer nicht daran interessiert ist der GUID des Moduls\).  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)