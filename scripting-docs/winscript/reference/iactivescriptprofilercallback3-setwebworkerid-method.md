---
title: "IActiveScriptProfilerCallback3::SetWebWorkerId-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerCallback3::SetWebWorkerId-Methode
Benachrichtigt den Profiler über die Worker ID, um für diese Profilerstellungssitzung zu verwenden.  Wenn die Funktion nicht im Kontext der Seite ausgeführt wird, wird diese Methode nicht aufgerufen.  Der Wert von `webWorkerId` Inkrementen von 1 für jeden Worker, beginnend bei 1.  Die ID\-Werte werden nicht dazu, die zu einer Sitzung hinaus stabil sein und entsprechen nur auf die Reihenfolge, in der die Worker erstellt wurden.  
  
## Syntax  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### Parameter  
 `webWorkerId`  
 Die ID Internet\-Worker  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.