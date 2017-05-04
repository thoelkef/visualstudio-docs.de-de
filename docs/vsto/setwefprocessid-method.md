---
title: "SetWefProcessId-Methode | Microsoft Docs"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# SetWefProcessId-Methode
  Stellt die Prozess\-ID bereit, die Inhalt des Internet\-Erweiterungs\-Frameworks \(WEF\) ausführt.  
  
## Syntax  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*dwProcessId*|Die Prozess\-ID, die verwendet wird, um WEF\-Inhalt auszuführen.|  
  
## Rückgabewert  
 Ein HRESULT\-Wert, der angibt, ob die Methode erfolgreich ausgeführt wurde.  
  
## Hinweise  
 Diese Methode muss aufgerufen werden, nachdem der WEF\-Inhaltsprozess erstellt, jedoch bevor ein WEF\-Inhalt ausgeführt wird.  
  
 Wenn Sie die Entwicklungsumgebung einen Debugger an den WEF\-Inhaltsprozess anfügen möchten, muss die Umgebung den Vorgang in der Implementierung dieser Methode ausführen.  
  
  