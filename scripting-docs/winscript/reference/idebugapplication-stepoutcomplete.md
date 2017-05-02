---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
Benachrichtigt den Debug\- ProzessManager, dass ein Sprachmodul im einschrittigen Modus im Begriff ist, an dessen Aufrufer zurückzukehren.  
  
## Syntax  
  
```  
HRESULT StepOutComplete();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Sprachmodule rufen diese Methode im einschrittigen Modus auf, bevor sie an ihrem Aufrufer zurückgeben.  Der Debug\- ProzessManager verwendet diese Möglichkeit, alle anderen Skriptmodule zu benachrichtigen, dass sie mit der ersten Möglichkeit unterbrechen sollten.  Diese Technik ist, wie sprachübergreifende Schrittmodi implementiert werden.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)