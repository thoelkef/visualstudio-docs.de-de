---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::put_registerValue-Methode"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt den Wert eines Registers festgelegt.  
  
## Syntax  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Parameter  
 `index`  
 \[in\]  Ein Wert aus der [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)\-Enumeration, der das Register angibt, in die geschrieben werden soll.  
  
 `NewVal`  
 \[in\]  Der neue Wert des Registers.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Trotz der Größe des Werts, sollte eine Implementierung nur gespeichert werden, was das Register normalerweise enthält.  Beispielsweise wird ein 8\-Bit\-Register nur das niedrigste 8\-Bit des angegebenen Werts enthalten.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)