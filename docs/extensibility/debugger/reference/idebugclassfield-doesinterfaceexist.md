---
title: "IDebugClassField::DoesInterfaceExist | Microsoft Docs"
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
  - "IDebugClassField::DoesInterfaceExist"
helpviewer_keywords: 
  - "IDebugClassField::DoesInterfaceExist-Methode"
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.  
  
## Syntax  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```c#  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### Parameter  
 `pszInterfaceName`  
 \[in\]  Eine Zeichenfolge, die den Namen der Schnittstelle enthält, nach denen gesucht werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurückgibt, S\_FALSE zurück, wenn die Schnittstelle nicht vorhanden ist. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode in Wirklichkeit eine Enumeration aller Schnittstellen ab und sucht in der Liste nach einer übereinstimmenden Schnittstelle.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)