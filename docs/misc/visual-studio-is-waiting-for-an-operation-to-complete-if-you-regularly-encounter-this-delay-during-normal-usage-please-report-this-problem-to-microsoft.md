---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A002A"
  - "vs.message.VB_E_IDWOLENOTRESPONDING"
ms.assetid: 0a4efbb7-72de-43a8-a51a-4a7a24ec743a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft.
Die Serveranwendung hat die aktuelle Anforderung nicht abgeschlossen.  
  
 Dieser Fehler könnte auch von Antivirensoftware verursacht werden, die Prozesse von devenv.exe blockiert.  Einige im Produkt enthaltene Features verwenden Skripts, und diese Skripts werden u. U. durch Antivirensoftware blockiert.  Verwandte Informationen finden Sie online unter "PRB: Visual IDE does not open when started or application cannot start error message" und der Adresse [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;306905&Product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;en-us;306905&Product=vsnet) \(auf Englisch\).  
  
### So beheben Sie diesen Fehler  
  
-   Wählen Sie **Wechseln zu** aus, um die Anwendung zu öffnen und das Problem zu untersuchen.  
  
     \- oder \-  
  
     Wählen Sie **Wiederholen** aus, um abzuwarten, bis die Serveranwendung die Verarbeitung der Anforderung fertig gestellt hat.  
  
### So korrigieren Sie durch Antivirensoftware hervorgerufene Fehler  
  
-   Legen Sie in der Antivirensoftware fest, dass die Software die Ausführung von Skripts von devenv.exe zulässt.  Ausführliche Anweisungen finden Sie in der Produktdokumentation zur Antivirensoftware.