---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
Der Active Script\-Host ruft diese Methode auf, um die Garbage Collection zu starten.  
  
## Syntax  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### Parameter  
 `scriptgctype`  
 \[in\] [SCRIPTGCTYPE\-Enumeration](../../winscript/reference/scriptgctype-enumeration.md), das angibt, ob normale oder vollständige Garbage Collection ausführt.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  
  
## Siehe auch  
 [IActiveScriptGarbageCollector\-Schnittstelle](../../winscript/reference/iactivescriptgarbagecollector-interface.md)