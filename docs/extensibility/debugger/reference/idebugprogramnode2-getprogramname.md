---
title: "IDebugProgramNode2::GetProgramName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetProgramName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetProgramName"
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```c#  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### Parameter  
 `pbstrProgramName`  
 \[out\]  Gibt den Namen des Programms zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Name eines Programms ist nicht die gleiche Aufgabe wie der Pfad zum Programm, obwohl der Name des Programms möglicherweise Teil eines solchen Pfads ist.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CProgram`\-Objekt implementiert, das die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle implementiert.  Die `MakeBstr`\-Funktion ordnet eine Kopie der angegebenen Zeichenfolge als BSTR.  
  
```cpp#  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)