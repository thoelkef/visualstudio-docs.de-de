---
title: "IJsDebugFrame-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugFrame-Schnittstelle
Stellt einen Stapelrahmen dar.  
  
## Syntax  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## Member  
  
### Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|------------------|  
|[IJsDebugFrame::Evaluate\-Methode](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Werten Sie einen Ausdruck im Kontext dieses Stapelrahmens aus.|  
|[IJsDebugFrame::GetDebugProperty\-Methode](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Gibt einen Eigenschaftenbrowser für diesen Stapelrahmen zurück.|  
|[IJsDebugFrame::GetDocumentPositionWithId\-Methode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.|  
|[IJsDebugFrame::GetDocumentPositionWithName\-Methode](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.|  
|[IJsDebugFrame::GetName\-Methode](../../winscript/reference/ijsdebugframe-getname-method.md)|Ruft den benutzerfreundlichen Namen des Stapelrahmens ab.|  
|[IJsDebugFrame::GetReturnAddress\-Methode](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Ruft die Rückgabeadresse ab, die beim "Start" des Frames mit "Push" übertragen wird \(siehe GetStackRange\).|  
|[IJsDebugFrame::GetStackRange\-Methode](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Gibt den Bereich der absoluten Adresse des logischen JavaScript\-Stapelrahmens zurück.|  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)