---
title: PROFILER_EXTERNAL_OBJECT_ADDRESS-Typ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9642a4a-f1fd-408a-9de6-e51562337bf1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b5708dfb0ad5e419f217d6d06a3c2b039d55b35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831557"
---
# <a name="profilerexternalobjectaddress-type"></a>PROFILER_EXTERNAL_OBJECT_ADDRESS-Typ
Die externe Objektadresse eines Objekts, z. B. eine reservierte C++-Objekt, das außerhalb der JavaScript-Heap befindet. Verwendet [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) und [PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef void* PROFILER_EXTERNAL_OBJECT_ADDRESS;  
```