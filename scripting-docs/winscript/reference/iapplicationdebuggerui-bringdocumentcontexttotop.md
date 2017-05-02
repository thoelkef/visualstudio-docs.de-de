---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentContextToTop"
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentContextToTop
Setzt das Fenster, das den Kontext des bestimmten Dokuments zur oben in der Debuggerbenutzeroberfläche enthält und führt das Fenster den Kontext aus.  
  
## Syntax  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### Parameter  
 `pddc`  
 \[in\] Dokumentieren Sie Kontext, um zur oben in der Debuggerbenutzeroberfläche einzubinden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Der Kontext, der von `pddc` angegeben wird, ist nicht bekannt.|  
  
## Hinweise  
 Diese Methode wird das Fenster, das den Kontext des bestimmten Dokuments zur oben in der Debuggerbenutzeroberfläche enthält und führt das Fenster den Kontext aus.  
  
## Siehe auch  
 [IApplicationDebuggerUI\-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)