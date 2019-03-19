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
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146434"
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