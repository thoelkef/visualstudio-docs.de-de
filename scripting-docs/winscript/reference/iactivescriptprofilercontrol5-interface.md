---
title: IActiveScriptProfilerControl5-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0c8b464004337b41280d6d19821f0fb9f1f50a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5-interface"></a>IActiveScriptProfilerControl5-Schnittstelle
Bietet eine Methode zur Aufzählung von GC-Heapobjekten, die einem Skriptmodul zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>Methoden  
 [IActiveScriptProfilerControl5::EnumHeap2-Methode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Gibt eine Schnittstelle zurück ([IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), der zum Durchlaufen der GC-heapobjekten im Kontext des Datenbankmoduls zugeordnete Skript verwendet werden kann.