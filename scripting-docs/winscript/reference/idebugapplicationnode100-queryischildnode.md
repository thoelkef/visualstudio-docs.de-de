---
title: "IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::QueryIsChildNode"
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationNode100::QueryIsChildNode
Bestimmt, ob das angegebene Dokument auf einen der untergeordneten Knoten des Knotens gehört.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100\-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md) wird durch PDM v10.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT QueryIsChildNode(  
        [in] IDebugDocument* pSearchKey  
        );  
```  
  
#### Parameter  
 `pSearchKey`  
 Der Suchbegriff.  
  
## Siehe auch  
 [IDebugApplicationNode100\-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md)