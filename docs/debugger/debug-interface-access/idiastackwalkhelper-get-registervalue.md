---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::get_registerValue-Methode"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Wert eines Registers ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `index`  
 \[in\]  Ein Wert vom [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)\-Enumeration angeben, dem abzurufenden registrieren Sie den Wert aus.  
  
 `pRetVal`  
 \[out\]  Gibt den aktuellen Wert des Registers zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Trotz der Größe des `pRetVal`\-Parameters, sollte eine Implementierung nur gespeichert werden, was das Register normalerweise enthält.  Zum Beispiel enthält ein 8\-Bit\-Register nur das niedrigste 8\-Bit des angegebenen Werts an.  Dieser 8\-Bit\-Wert wird dem 64\-Bit erweitert, wenn er von dieser Methode zurückgegeben wird.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e\-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)