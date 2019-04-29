---
title: IActiveScriptProfilerControl5-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dacca8e8bf161b6f3a84dc216596673d5df8258c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992905"
---
# <a name="iactivescriptprofilercontrol5-interface"></a>IActiveScriptProfilerControl5-Schnittstelle
Bietet eine Methode zur Aufzählung von GC-Heapobjekten, die einer Skript-Engine zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>Methoden  
 [IActiveScriptProfilerControl5::EnumHeap2-Methode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Gibt eine Schnittstelle zurück ([IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), der zum Durchlaufen der GC-Heapobjekte im Kontext des zugeordneten Skriptmoduls verwendet werden kann.