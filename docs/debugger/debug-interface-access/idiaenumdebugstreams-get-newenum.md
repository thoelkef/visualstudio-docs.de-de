---
title: "IDiaEnumDebugStreams::get__NewEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreams::get__NewEnum-Methode"
ms.assetid: 972372ff-abfc-4987-a302-7788fab90348
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreams::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>\-Version dieses Enumerators ab.  
  
## Syntax  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Parameter  
 pRetVal  
 \[out\]  Gibt die `IUnknown`\-Schnittstelle zurück, die die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>\-Version dieses Enumerators darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)