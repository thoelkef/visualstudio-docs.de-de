---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
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
  - "IDiaStackFrame::get_rawLVarInstanceValue-Methode"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft den Wert der angegebenen lokalen Variable als unformatierte Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### Parameter  
 `pInstance`  
 \[in\]  Ein `IDiaLVarInstance`\-Objekt, das eine Instanz der lokalen Variablen darstellt, in der der Wert abgerufen werden soll.  
  
 `cbDataMax`  
 \[in\]  Maximale Anzahl von Bytes im Puffer wurden durch `pbData`auf.  Dies kann maximal 8 Byte \(`sizeof(ULONGLONG)`\) sein.  
  
 `pcbData`  
 \[out\]  Gibt die tatsächliche Anzahl von Bytes zurück, die im Puffer gespeichert werden.  
  
 `pbData`  
 \[out\]  Ein Puffer mit Daten gefüllt werden sollen.  Darf nicht `NULL` sein.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)