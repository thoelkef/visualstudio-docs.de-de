---
title: IActiveScriptProfilerControl5-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b20afd05116a98e81a3eeea82e83e6ed200c44a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349282"
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