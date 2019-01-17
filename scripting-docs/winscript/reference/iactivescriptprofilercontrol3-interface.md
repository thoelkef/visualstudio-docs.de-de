---
title: IActiveScriptProfilerControl3-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bebe351608b3136ac00a059bffab3535141e7fca
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344719"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3-Schnittstelle
Bietet eine Methode zur Aufzählung von GC-Heapobjekten, die einer Skript-Engine zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>Methoden  
 [IActiveScriptProfilerControl3::EnumHeap Method](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Gibt eine Schnittstelle zurück ([IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), der zum Durchlaufen der GC-Heapobjekte im Kontext des zugeordneten Skriptmoduls verwendet werden kann.