---
title: "IDebugClassField::EnumInterfacesImplemented | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumInterfacesImplemented"
helpviewer_keywords: 
  - "IDebugClassField::EnumInterfacesImplemented-Methode"
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die Schnittstellen, die von dieser Klasse implementiert werden.  
  
## Syntax  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der implementierten Schnittstellen darstellt.  Gibt einen NULL\-Wert zurück, wenn keine Schnittstellen bestehen.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine Schnittstellen gibt, die von dieser Klasse implementiert werden.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)\-Objekt, das eine Schnittstelle beschreibt.  Beachten Sie, dass nicht verwalteten Schnittstellen [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code nicht verwendet, während eine einzelne Entität sodass diese Methode immer einen NULL\-Wert für nicht verwalteten Code [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] zurückgibt.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)