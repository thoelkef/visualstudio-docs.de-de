---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
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
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Zerstört die eindeutige ID, die dieser Eigenschaft zugeordnet wird und angibt, dass der Aufrufer nicht mehr relevant, um diese Eigenschaft aller anderen Eigenschaften eindeutig zu identifizieren.  
  
## Syntax  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn das Debugmodul nicht eindeutige ID für eine Eigenschaft zu unterstützen \(da sie bereits verfolgt intern eindeutig\), kann es leicht `E_NOTIMPL` für diese Methode zurückgeben.  
  
 Eindeutige ID wird mit einem Aufruf der [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)\-Methode erstellt, wenn der Aufrufer überprüft werden soll, ob diese Eigenschaft für alle anderen Eigenschaften eindeutig identifiziert wird.  
  
## Siehe auch  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)