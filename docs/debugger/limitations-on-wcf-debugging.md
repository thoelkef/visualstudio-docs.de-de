---
title: "Einschr&#228;nkungen beim WCF-Debugging | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen, WCF"
  - "WCF, Einschränkungen des Debuggers"
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Einschr&#228;nkungen beim WCF-Debugging
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden drei Möglichkeiten stehen Ihnen zur Verfügung, um das Debuggen eines WCF\-Diensts zu starten:  
  
-   Sie debuggen einen Clientprozess, durch den ein Dienst aufgerufen wird.  Der Debugger führt einen Einzelschritt in den Dienst aus.  Der Dienst muss sich nicht in derselben Projektmappe wie die Clientanwendung befinden.  
  
-   Sie debuggen einen Clientprozess, der eine Anforderung an einen Dienst sendet.  Der Dienst muss Teil der Projektmappe sein.  
  
-   Sie verwenden die Option **An den Prozess anhängen**, um den Debugger an einen gerade ausgeführten Dienst anzuhängen.  Das Debuggen wird im Dienst gestartet.  
  
 In diesem Thema werden Einschränkungen dieser Szenarien beschrieben.  
  
## Einschränkungen bei der schrittweisen Verwendung eines Diensts  
 Folgende Bedingungen müssen erfüllt sein, damit Sie von den debuggten Clientanwendungen einen Einzelschritt in einen Dienst ausführen können:  
  
-   Der Client muss den Dienst aufrufen, indem er ein synchrones Clientobjekt verwendet.  
  
-   Die Vertragsoperation darf nicht unidirektional sein.  
  
-   Wenn es sich um einen asynchronen Server handelt, können Sie nicht die vollständige Aufrufliste anzeigen, während der Code innerhalb des Diensts ausgeführt wird.  
  
-   Das Debuggen muss mithilfe des folgenden Codes in der Datei "app.config" oder "Web.config" aktiviert werden:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Dieser Code muss nur einmal hinzugefügt werden.  Sie können diesen Code hinzufügen, indem Sie die CONFIG\-Datei bearbeiten oder den Debugger mithilfe der Option **An den Prozess anhängen** an den Dienst anhängen.  Wenn Sie **An den Prozess anhängen** für einen Dienst verwenden, wird der Debugcode automatisch der CONFIG\-Datei hinzugefügt.  Anschließend können Sie das Debuggen starten und einen Einzelschritt in den Dienst ausführen, ohne die CONFIG\-Datei bearbeiten zu müssen.  
  
## Einschränkungen beim Ausführen bis Rücksprung in einem Dienst  
 Das Ausführen bis Rücksprung in einem Dienst und zurück zum Client unterliegt denselben Einschränkungen wie das Ausführen von Einzelschritten in einen Dienst.  Außerdem muss der Debugger an den Client angehängt werden.  Wenn Sie einen Client debuggen und einen Einzelschritt in einen Dienst ausführen, bleibt der Debugger am Dienst angehängt.  Dies gilt unabhängig davon, ob Sie den Client über **Debuggen starten** gestartet oder den Debugger über **An den Prozess anhängen** an den Client angehängt haben.  Falls Sie das Debuggen durch Anhängen an den Dienst gestartet haben, wurde der Debugger bis jetzt noch nicht an den Client angehängt.  Wenn Sie die Ausführung bis Rücksprung im Dienst und zurück zum Client vornehmen, müssen Sie in diesem Fall zuerst **An den Prozess anhängen** verwenden, um den Debugger manuell an den Client anzuhängen.  
  
## Einschränkungen beim automatischen Anfügen an einen Dienst  
 Das automatische Anfügen an einen Dienst unterliegt folgenden Einschränkungen:  
  
-   Der Dienst muss Teil der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe sein, die Sie debuggen.  
  
-   Der Dienst muss gehostet werden.  Er kann Teil eines Websiteprojekts \(Dateisystem und HTTP\), eines Webanwendungsprojekts \(Dateisystem und HTTP\) oder eines WCF\-Dienstbibliotheksprojekts sein.  WCF\-Dienstbibliotheksprojekte können entweder Dienstbibliotheken oder Workflowdienstbibliotheken sein.  
  
-   Der Dienst muss über einen WCF\-Client aufgerufen werden.  
  
-   Das Debuggen muss mithilfe des folgenden Codes in der Datei "app.config" oder "Web.config" aktiviert werden:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## Lokales Hosten  
 Ein *lokal gehosteter Dienst* ist ein WCF\-Dienst, der nicht innerhalb von IIS, WCF\-Diensthost oder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server ausgeführt wird.  Weitere Informationen zum Debuggen eines lokal gehosteten Diensts finden Sie unter [Gewusst wie: Debuggen eines lokal gehosteten WCF\-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## Lokales Hosten  
 Um das Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0\- oder 3.5\-Anwendungen zu aktivieren, muss [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 oder 3.5 vor der Installation von [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] installiert werden.  Wenn [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] vor [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 oder 3.5 installiert wird, tritt ein Fehler auf, wenn Sie versuchen, eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0\- oder 3.5\-Anwendung zu debuggen.  Die Fehlermeldung lautet: "Automatischer Einzelschritt auf dem Server nicht möglich." Verwenden Sie zum Beheben dieses Problems **Systemsteuerung**, **Programme und Funktionen**, um die [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]\-Installation zu reparieren.  
  
## Siehe auch  
 [Debuggen von WCF\-Diensten](../debugger/debugging-wcf-services.md)   
 [Gewusst wie: Debuggen eines lokal gehosteten WCF\-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)