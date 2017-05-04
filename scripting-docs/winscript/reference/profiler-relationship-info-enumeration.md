---
title: "PROFILER_RELATIONSHIP_INFO-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_RELATIONSHIP_INFO-Enumeration
Enthält Informationen über das Objekt in der Beziehung dar.  Wird in [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md) verwendet.  
  
## Syntax  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|Das Objekt ist eine Zahl.|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|Das Objekt ist eine Zeichenfolge.|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|Das Objekt ist ein Heapobjekt.|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|Das Objekt ist also. nicht auf dem Garbage Collection\-Heap extern.|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|Das Objekt ist ein BSTR.|