---
title: "Fehler: Das Debuggen ist nicht m&#246;glich, da ein Kerndebugger auf dem System aktiviert ist | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.kernel_dbg_enabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Kernel-Debugger"
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Das Debuggen ist nicht m&#246;glich, da ein Kerndebugger auf dem System aktiviert ist
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Debuggen von verwaltetem Code kann die folgende Fehlermeldung ausgegeben werden:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Diese Meldung wird angezeigt, wenn Sie versuchen, verwalteten Code zu debuggen:  
  
-   auf einem [!INCLUDE[win7](../debugger/includes/win7_md.md)]\- oder [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]\-System, das im Debugmodus gestartet wurde.  
  
-   Die Anwendung verwendet die CLR\-Version 2.0, 3.0 oder 3.5.  
  
## Lösung  
  
#### So beheben Sie dieses Problem  
  
-   Aktualisieren Sie die Anwendung auf CLR\-Version 4.0 oder 4.5.  
  
     – oder –  
  
-   Deaktivieren Sie Kerneldebugging, und debuggen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     – oder –  
  
-   Debuggen Sie mit dem Kerneldebugger anstatt mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     – oder –  
  
-   Deaktivieren Sie im Kerneldebugger die Benutzermodusausnahmen.  
  
#### So deaktivieren Sie Kerneldebugging in der aktuellen Sitzung  
  
-   Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### So deaktivieren Sie Kerneldebugging für alle Sitzungen \(Windows Vista und Windows 7\)  
  
1.  Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Starten Sie den Computer neu.  
  
#### So deaktivieren Sie Kerneldebuggen für alle Sitzungen \(andere Windows\-Betriebssysteme\)  
  
1.  Suchen Sie die Datei "boot.ini" auf dem Systemlaufwerk \(normalerweise C:\\\).  Die Datei "boot.ini" ist möglicherweise versteckt installiert und schreibgeschützt.  Verwenden Sie zur Anzeige der Datei daher folgenden Befehl:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Öffnen Sie "boot.ini" im Editor, und entfernen Sie die folgenden Optionen:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Starten Sie den Computer neu.  
  
#### So debuggen Sie mit dem Kerneldebugger  
  
1.  Wenn der Kerneldebugger verknüpft ist, werden Sie in einer Meldung gefragt, ob Sie das Debuggen fortsetzen möchten.  Klicken Sie auf die Schaltfläche, um den Vorgang fortzusetzen.  
  
2.  Sie erhalten möglicherweise einen `User break exception(Int 3).`\-Wert. Geben Sie in diesem Fall den folgenden Befehl für den Kerneldebugger ein, um das Debuggen fortzusetzen:  
  
     `gn`  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)