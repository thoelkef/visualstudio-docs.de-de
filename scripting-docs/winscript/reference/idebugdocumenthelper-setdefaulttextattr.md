---
title: "IDebugDocumentHelper::SetDefaultTextAttr | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDefaultTextAttr
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDefaultTextAttr"
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDefaultTextAttr
Legt die Standardattribute fest, um für Text zu verwenden, der nicht in einem Skriptblock ist.  
  
## Syntax  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### Parameter  
 `staTextAttr`  
 Die Standardquelltextattribute.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Es sei denn, die Standardattribute so geändert werden, ist die Standardattribute für Text außerhalb eines Skriptblocks SOURCETEXT\_ATTR\_NONSOURCE.  Die Benutzeroberfläche kann diese Informationen verwenden, um Text außerhalb der Skriptblöcke zu markieren, als schreibgeschützt.  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [SOURCE\_TEXT\_ATTR\-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)