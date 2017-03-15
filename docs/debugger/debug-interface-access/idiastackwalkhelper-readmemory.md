---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory-Methode"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest einen Block von Daten aus dem Bild der ausführbaren Datei im Arbeitsspeicher.  
  
## Syntax  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### Parameter  
 `type`  
 \[in\]  Ein Wert aus der [MemoryTypeEnum\-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)\-Enumeration, der den Typ des zu lesenden Arbeitsspeichers angibt.  
  
 VA  
 \[in\]  Virtuelle Adresse im Bild, ab dem gelesen werden soll.  
  
 `cbData`  
 \[in\]  Die Größe in Bytes im Datenpuffer.  
  
 `pcbData`  
 \[out\]  Gibt die Anzahl der gelesenen Bytes, die tatsächlich zurückgegeben werden.  Wenn `pbData``NULL`ist, ist dies die Gesamtzahl von Bytes verfügbaren Daten.  
  
 `pbData`  
 \[in, out\]  Ein Puffer, der dem Arbeitsspeicher lesen gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum\-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)