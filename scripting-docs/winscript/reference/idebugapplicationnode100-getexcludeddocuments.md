---
title: "IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::GetExcludedDocuments"
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::GetExcludedDocuments
Ruft die Textdokumente ab, die von den angegebenen Filter ausgeblendet werden.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100\-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md) wird durch PDM v10.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT GetExcludedDocuments(  
        [in] APPLICATION_NODE_EVENT_FILTER filter,  
        [out] TEXT_DOCUMENT_ARRAY* pDocuments  
        );  
```  
  
#### Parameter  
 `filter`  
 Der Filter.  
  
 `pDocuments`  
 Der Satz von Dokumenten.  
  
## Siehe auch  
 [IDebugApplicationNode100\-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md)