---
title: "IDebugDocument2::GetName | Microsoft Docs"
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
  - "IDebugDocument2::GetName"
helpviewer_keywords: 
  - "IDebugDocument2::GetName"
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocument2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des Dokuments in einem von mehreren Formularen ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### Parameter  
 `gnType`  
 \[in\]  Ein Wert aus der [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)\-Enumeration, der den Typ des Titels bestimmt, die zurückgegeben werden soll.  
  
 `pbstrFileName`  
 \[out\]  Gibt eine Zeichenfolge zurück, die den Dokumentnamen enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode kann den Namen des Dokuments als Name oder als Dateiname oder sogar Teil eines Dateinamens zurückgeben, z.  
  
## Siehe auch  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)