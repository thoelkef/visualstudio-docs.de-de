---
title: "Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgem&#228;&#223; konfiguriert ist | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgem&#228;&#223; konfiguriert ist
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Dieser Fehler tritt auf, wenn der Name des Hostcomputers für den Visual Studio\-Debugger vom Zielcomputer nicht aufgelöst werden kann.  Überprüfen Sie die DNS\-Einstellungen auf dem Zielcomputer.  
  
-   Gehen Sie wie folgt vor, um Informationen zum Anzeigen der DNS\-Einstellung in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oder Windows Server 2008 R einzublenden: Wählen Sie im Menü **Start** die Option **Hilfe und Support** aus, und suchen Sie anschließend nach Änderungen der TCP\/IP\-Einstellungen.  
  
-   Um weitere Informationen hierzu zu erhalten, rufen Sie die [Microsoft Windows\-Website](http://go.microsoft.com/fwlink/?LinkId=252720) auf, und suchen Sie nach Änderungen der TCP\/IP\-Einstellungen.  
  
 Wenn das DNS\-Problem nicht behoben werden kann, können Sie versuchen, den Remotedebugger unter einem anderen Konto auszuführen.  Dieser Fehler tritt nur auf, wenn der Remotedebugger unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird.  Wenn Sie den Remotedebugger unter einem anderen Konto ausführen, kann die NTLM\-Authentifizierung verwendet werden, für die DNS nicht erforderlich ist.  .  Das Verfahren finden Sie unter [Fehler: Der Visual Studio\-Remotedebugdienst auf dem Zielcomputer kann keine Rückverbindung mit diesem Computer herstellen](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).