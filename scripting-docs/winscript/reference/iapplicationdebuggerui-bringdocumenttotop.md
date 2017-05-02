---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
Setzt das Fenster, das das angegebene enthält, debuggen Dokument zur oben in der Debuggerbenutzeroberfläche.  
  
## Syntax  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### Parameter  
 `pddt`  
 \[in\] Debuggen Sie Dokument, um zur oben in der Debuggerbenutzeroberfläche einzubinden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Das Dokument nicht bekannt.|  
  
## Hinweise  
 Diese Methode wird das Fenster, das das angegebene enthält, debuggen Dokument zur oben in der Debuggerbenutzeroberfläche.  
  
## Siehe auch  
 [IApplicationDebuggerUI\-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)