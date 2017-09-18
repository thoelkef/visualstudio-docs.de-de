---
title: "IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die attributierten Informationen als BLOB von Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```c#  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### Parameter  
 `ppBlob`  
 \[in, out\]  Ein Array, das die Attributdaten gefüllt wird.  
  
 `pdwLen`  
 \[in, out\]  Gibt die maximale Anzahl von Bytes an, die im `ppBlob` Array zurückzukehren und gibt die Anzahl von Bytes zurück, die sich tatsächlich in das Array geschrieben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Legen Sie den `ppBlob`\-Parameter zu einem NULL\-Wert fest, um die Anzahl der Attributdaten verfügbar.  Anschließend ordnen Sie ein Array, und übergeben Sie das Array in `ppBlob` für den Parameter.  
  
 Die Attributdaten stellen die unformatierten Daten des benutzerdefinierten Attributs dar.  
  
## Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)