---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
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
  - "IDiaSession::put_loadAddress-Methode"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt die Ladeadresse für die ausführbare Datei fest, die auf Symbole in diesem Symbolspeicher entspricht.  
  
## Syntax  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### Parameter  
 `NewVal`  
 \[in\]  Ladeadresse für die ausführbare Datei.  
  
## Hinweise  
 Eigenschaften von virtuellen Adresse des Symbols \(VA\) werden mithilfe des Werts dieser Methode berechnet.  Virtuelle Adressen werden nicht berechnet, es sei denn, diese Eigenschaft auf den Wert ungleich 0 \(null\) festgelegt ist.  
  
> [!NOTE]
>  Sie müssen diese Methode aufrufen, wenn Sie das [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Objekt abrufen und bevor Sie die Verwendung des Objekts beginnen, wenn Sie alle virtuellen Eigenschaften für Symbole verwenden müssen.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)