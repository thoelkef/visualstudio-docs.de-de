---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt eine eindeutige ID für diese Eigenschaft wird sichergestellt, dass sie von allen anderen Eigenschaften eindeutig ist.  
  
## Syntax  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird aufgerufen, wenn der Debug\- Manager der Sitzung überprüfen möchte, ob diese Eigenschaft für alle anderen Eigenschaften eindeutig identifiziert wird.  Das Debugmodul \(DE\) unterstützt diese Methode, es sei denn, mit Eigenschaften, die sie behandelt, sind bereits eindeutig identifiziert.  Wenn DE diese Methode nicht unterstützt wird, gibt sie `E_NOTIMPL`zurück.  
  
 Jede eindeutige ID, die `CreateObjectID` erstellt wird, zerstört wird, wenn die [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)\-Methode aufgerufen wird. dies auch Signalisiert das Ende der Anforderung für diese Eigenschaft eindeutig identifizieren.  
  
> [!NOTE]
>  Es gibt keine Möglichkeit, um diese abzurufen, sodass der eindeutigen ID DE tun, was dies für eindeutige ID, wenn die `CreateObjectID`\-Methode aufgerufen wird.  
  
## Siehe auch  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)