---
title: "IDispatchEx::GetNameSpaceParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNameSpaceParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNameSpaceParent-Methode"
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNameSpaceParent
Ruft die Schnittstelle für das Namespaceübergeordnetes Elemente übergeordnete Ebene eines Objekts ab.  
  
## Syntax  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### Parameter  
 `ppunk`  
 Adresse eines `IUnknown`\-Schnittstellenzeigers, der die Schnittstelle des Namespaceübergeordneten Datensätze empfängt.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder ein OLE\-definierter Fehlercode andernfalls.  
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)