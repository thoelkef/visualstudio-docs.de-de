---
title: "IDebugDocumentHelper::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.BringDocumentContextToTop
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::BringDocumentContextToTop"
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::BringDocumentContextToTop
Setzt einen Kontext dieses Dokuments zur oben in der Debuggerbenutzeroberfläche.  
  
## Syntax  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### Parameter  
 `pddc`  
 Dokumentieren Sie Kontext, um zur oben in der Debuggerbenutzeroberfläche einzubinden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode führt einen Kontext dieses Dokuments zur oben in der Debuggerbenutzeroberfläche.  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)