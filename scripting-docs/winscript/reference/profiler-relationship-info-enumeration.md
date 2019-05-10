---
title: PROFILER_RELATIONSHIP_INFO-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808892"
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO-Enumeration
Stellt Informationen über das Objekt in der Beziehung dar. Verwendet [PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|Das Objekt ist eine Zahl.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|Das Objekt ist eine Zeichenfolge.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|Das Objekt ist ein heapobjekt.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Das Objekt ist extern und, also nicht auf die Garbage Collection-Heap.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|Das Objekt ist ein BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|Das Objekt ist eine TEILZEICHENFOLGE.|