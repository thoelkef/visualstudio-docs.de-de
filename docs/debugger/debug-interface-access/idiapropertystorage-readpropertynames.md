---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft entsprechende Zeichenfolgennamens für den angegebenen Eigenschaftenbezeichner ab.  
  
## Syntax  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### Parameter  
 `cpropid`  
 \[in\]  Eigenschaft\-ID Zahl in `rgpropid`.  
  
 `rgpropid`  
 \[in\]  Eigenschaft\-ID Array, für die die Namen abgerufen werden \(`PROPID` wird in WTypes.h als `ULONG`definiert\).  
  
 `rglpwstrName`  
 \[in, out\]  Array von Eigenschaftennamen für die angegebene Eigenschaft\-ID.  Das Array muss zugeordnet werden, um die angeforderte Anzahl von Eigenschaftennamen enthalten und muss in der Lage sein, Zeichenfolgen `cpropid`mindestens`BSTR` aufzunehmen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Die zurückgegebenen Eigenschaftennamen müssen gemeinsam genutzt werden \(durch Aufrufen der `SysFreeString`\-Funktion\), wenn sie nicht mehr benötigt werden.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)