---
title: "IEEDataStorage::GetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage::GetData"
helpviewer_keywords: 
  - "IEEDataStorage::GetData"
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die angegebene Anzahl von Bytes aus dem Objekt ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```c#  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### Parameter  
 `dataSize`  
 \[in\]  Die Anzahl der abzurufenden Bytes \(das `data` Array muss mindestens diese Anzahl von Bytes\) enthalten.  
  
 `sizeGotten`  
 \[out\]  Gibt die Anzahl der Bytes, die tatsächlich abgerufenen zurück.  
  
 `data`  
 \[in, out\]  Bei den angeforderten Daten zu füllende Array.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der empfohlene Verwendung dieser Methode besteht darin, alle Bytes der Daten in ein lokales Array abzurufen, da es keine Möglichkeit gibt, in Bytes zum Abrufen des Prozesses zu überspringen.  In diesem Fall sollte der Parameter `dataSize` der Wert sein, der von der [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)\-Methode zurückgegeben wird.  
  
## Siehe auch  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)