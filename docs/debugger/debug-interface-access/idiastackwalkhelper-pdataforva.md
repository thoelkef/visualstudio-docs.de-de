---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::pdataByVA-Methode"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den PDATA\-Bezugspunkt Datenbindungsausdrücken zurück, der der virtuelle Adresse zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### Parameter  
 `va`  
 \[in\]  Gibt die virtuelle Adresse der Daten an, die abgerufen werden sollen.  
  
 `cbData`  
 \[in\]  Die Größe von Daten in Bytes abzurufen.  
  
 `pcbData`  
 \[out\]  Gibt die tatsächliche Größe der Daten in Bytes zurück, das abgerufen wurde.  
  
 `pbData`  
 \[in, out\]  Ein Puffer, der den angeforderten Daten gefüllt wird.  Kann nicht `NULL` sein.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn keine PDATA für die angegebene Adresse gibt.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das PDATA \(.pdata mit dem Namen „im Abschnitt“\) einer Kompiliereinheit enthält Informationen zur Ausnahmebehandlung für Funktionen.  
  
 Der Aufrufer weiß, wie viele Daten zurückgegeben werden soll, sodass der Aufrufer keine Anforderung verfügt, um anzufordern, wie viele Daten verfügbar ist.  Daher ist es zulässig, eine Implementierung dieser Methode für ein Fehler zurückgegeben, wenn der `pbData`\-Parameter `NULL`ist.  
  
## Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)