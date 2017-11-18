---
title: "Einschränkungen beim WCF-Debugging | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72e166d5501849dd84964364a94b2bdf6dc239a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="limitations-on-wcf-debugging"></a>Einschränkungen beim WCF-Debugging
Die folgenden drei Möglichkeiten stehen Ihnen zur Verfügung, um das Debuggen eines WCF-Diensts zu starten:  
  
-   Sie debuggen einen Clientprozess, durch den ein Dienst aufgerufen wird. Der Debugger führt einen Einzelschritt in den Dienst aus. Der Dienst muss sich nicht in derselben Projektmappe wie die Clientanwendung befinden.  
  
-   Sie debuggen einen Clientprozess, der eine Anforderung an einen Dienst sendet. Der Dienst muss Teil der Projektmappe sein.  
  
-   Verwenden Sie **an den Prozess anhängen** an einen Dienst anfügen, die gerade ausgeführt wird. Das Debuggen wird im Dienst gestartet.  
  
 In diesem Thema werden Einschränkungen dieser Szenarien beschrieben.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Einschränkungen bei der schrittweisen Verwendung eines Diensts  
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
  
     Dieser Code muss nur einmal hinzugefügt werden. Sie können diesen Code hinzufügen, indem Sie die config-Datei bearbeiten oder durch Anfügen an den Dienst mithilfe **an den Prozess anhängen**. Bei Verwendung von **an den Prozess anhängen** für einen Dienst, wird der Debugcode automatisch zur .config-Datei hinzugefügt. Anschließend können Sie das Debuggen starten und einen Einzelschritt in den Dienst ausführen, ohne die CONFIG-Datei bearbeiten zu müssen.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Einschränkungen beim Ausführen bis Rücksprung in einem Dienst  
 Das Ausführen bis Rücksprung in einem Dienst und zurück zum Client unterliegt denselben Einschränkungen wie das Ausführen von Einzelschritten in einen Dienst. Außerdem muss der Debugger an den Client angehängt werden. Wenn Sie einen Client debuggen und einen Einzelschritt in einen Dienst ausführen, bleibt der Debugger am Dienst angehängt. Dies ist "true" gibt an, ob der Client mit gestartet **Debuggen** oder an den Client angehängt werden, mithilfe von **an den Prozess anhängen**. Falls Sie das Debuggen durch Anhängen an den Dienst gestartet haben, wurde der Debugger bis jetzt noch nicht an den Client angehängt. In diesem Fall, wenn Sie mit Schritt Rücksprung im Dienst und zurück an den Client verfügen, müssen Sie zuerst verwenden **an den Prozess anhängen** für die Verbindung an den Client manuell.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Einschränkungen beim automatischen Anfügen an einen Dienst  
 Das automatische Anfügen an einen Dienst unterliegt folgenden Einschränkungen:  
  
-   Der Dienst muss Teil der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe sein, die Sie debuggen.  
  
-   Der Dienst muss gehostet werden. Er kann Teil eines Websiteprojekts (Dateisystem und HTTP), eines Webanwendungsprojekts (Dateisystem und HTTP) oder eines WCF-Dienstbibliotheksprojekts sein. WCF-Dienstbibliotheksprojekte können entweder Dienstbibliotheken oder Workflowdienstbibliotheken sein.  
  
-   Der Dienst muss über einen WCF-Client aufgerufen werden.  
  
-   Das Debuggen muss mithilfe des folgenden Codes in der Datei "app.config" oder "Web.config" aktiviert werden:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Lokales Hosten  
 Ein *lokal gehosteter Dienst* ist ein WCF-Dienst, der nicht innerhalb von IIS, WCF-Diensthost ausgeführt werden kann oder der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Informationen über das Debuggen eines selbst gehosteten Diensts finden Sie unter [Vorgehensweise: Debuggen eines WCF-Diensts selbst gehostete](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Lokales Hosten  
 Zum Aktivieren des Debuggens von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 oder 3.5-Anwendungen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 oder 3.5 muss installiert werden, bevor [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] installiert ist. Wenn [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] installiert wurde, bevor [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 oder 3.5 ein Fehler auftritt, wenn Sie versuchen, Sie Debuggen eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 oder 3.5-Anwendung. Die Fehlermeldung lautet: "Automatischer Einzelschritt auf dem Server nicht möglich." Um dieses Problem zu beheben, verwenden Sie das Windows **Systemsteuerung** > **Programme und Funktionen** Reparieren Ihrer [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Installation.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)   
 [Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)