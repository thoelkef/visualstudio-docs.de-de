---
title: "Gewusst wie: Ausf&#252;hren eines Einzelschritts in WCF-Dienste | Microsoft Docs"
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
  - "WCF, Debuggen"
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Ausf&#252;hren eines Einzelschritts in WCF-Dienste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie einen Einzelschritt in einen WCF\-Dienst ausführen.  Wenn sich der WCF\-Dienst in derselben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe wie der Client befindet, erreichen Sie Haltepunkte innerhalb des WCF\-Dienstes.  
  
 Damit dies funktioniert, müssen Sie das Debuggen in der Datei app.config oder Web.config aktivieren.  Weitere Informationen zum Aktivieren des Debuggens sowie zu Einschränkungen beim Ausführen von Einzelschritten in WCF\-Dienste finden Sie unter [Einschränkungen beim WCF\-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### So führen Sie einen Einzelschritt in einen WCF\-Dienst aus  
  
1.  Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe, die sowohl den WCF\-Client als auch WCF\-Dienstprojekte enthält.  
  
2.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das WCF\-Clientprojekt, und klicken Sie dann auf **Als Startprojekt festlegen**.  
  
3.  Aktivieren Sie das Debuggen in der Datei app.config oder web.config.  Weitere Informationen finden Sie unter [Einschränkungen beim WCF\-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Setzen Sie an der Stelle im Clientprojekt, an der Sie die schrittweise Ausführung beginnen möchten, einen Haltepunkt.  Üblicherweise wird dies vor dem Aufruf des WCF\-Diensts sein.  
  
5.  Ausführen bis zum Haltepunkt, dann Beginnen der schrittweisen Ausführung.  Der Debugger führt die schrittweise Ausführung des Diensts automatisch durch.  
  
## Siehe auch  
 [Debuggen von WCF\-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF\-Debugging](../debugger/limitations-on-wcf-debugging.md)   
 [Gewusst wie: Debuggen eines lokal gehosteten WCF\-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)