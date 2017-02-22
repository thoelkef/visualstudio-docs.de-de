---
title: "IDiaSymbol::getSrcLineOnTypeDefn | Microsoft Docs"
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
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::getSrcLineOnTypeDefn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Quelldatei und die Zeilennummer ab, die angeben, wo ein angegebener benutzerdefinierter Typ definiert ist.  
  
## Syntax  
  
```cpp  
HRESULT getSrcLineOnTypeDefn(  
   IDiaLineNumber **ppResult);  
```  
  
#### Parameter  
 `ppResult`  
 \[out\] Objekt A `IDiaLineNumber`, das die Quelldatei und die Zeilennummer in der das benutzerdefinierte enthält.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)