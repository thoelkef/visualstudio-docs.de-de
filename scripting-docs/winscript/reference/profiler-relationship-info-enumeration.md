---
title: PROFILER_RELATIONSHIP_INFO-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e95b11537873d3bfe02bf3fa793b61ace10938aa
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095809"
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
|PROFILER_PROPERTY_TYPE_NUMBER|0 x 01|Das Objekt ist eine Zahl.|  
|PROFILER_PROPERTY_TYPE_STRING|0 x 02|Das Objekt ist eine Zeichenfolge.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0 x 03|Das Objekt ist ein heapobjekt.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Das Objekt ist extern und, also nicht auf die Garbage Collection-Heap.|  
|PROFILER_PROPERTY_TYPE_BSTR|0 x 05|Das Objekt ist ein BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0 x 06|Das Objekt ist eine TEILZEICHENFOLGE.|