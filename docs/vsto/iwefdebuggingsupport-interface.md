---
title: "IWefDebuggingSupport-Schnittstelle"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# IWefDebuggingSupport-Schnittstelle
  Wird von eine Debugumgebung, wie Visual Studio, um das Debuggen von Apps für Office erleichtern.  Die Office\-Anwendung, wie Word oder Excel, erhält diese Schnittstelle von Visual Studio und ruft dann Methoden auf der Schnittstelle an bestimmten Punkten während der Debugsitzung an.  
  
## Syntax  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## Methoden  
 In der folgenden Tabelle sind die Methoden auf, die die IWefDebuggingSupport\-Schnittstelle definiert.  
  
|Name|Description|  
|----------|-----------------|  
|[GetAutoInsertExtensions-Methode](../vsto/getautoinsertextensions-method.md)|Ruft Informationen über die Apps für Office ab, die während des Debuggens automatisch eingefügt werden sollen.|  
|[SetWefProcessId-Methode](../vsto/setwefprocessid-method.md)|Stellt die Prozess\-ID bereit, die Inhalt des Internet\-Erweiterungs\-Frameworks \(WEF\) ausführt.|  
  
  