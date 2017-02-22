---
title: "IDiaStackWalkHelper::imageForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::imageForVA-Methode"
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Anfang des Bilds einer ausführbaren Datei angegebene Adresse einer virtuellen Arbeitsspeicher im irgendwo im Speicherbereich der ausführbaren Datei zurück.  
  
## Syntax  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### Parameter  
 `vaContext`  
 \[in\]  Die virtuelle Adresse, die irgendwo im Raum der ausführbaren Datei befindet.  
  
 `pvaImageStart`  
 \[out\]  Gibt die virtuelle Adresse des Bilds Starten der ausführbaren Datei zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)