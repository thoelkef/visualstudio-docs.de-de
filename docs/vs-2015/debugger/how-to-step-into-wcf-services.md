---
title: 'Vorgehensweise: Schritt in WCF-Dienste | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176525"
---
# <a name="how-to-step-into-wcf-services"></a>Vorgehensweise: Ausführen eines Einzelschritts in WCF-Diensten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] können Sie einen Einzelschritt in einen WCF-Dienst ausführen. Wenn sich der WCF-Dienst in derselben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe wie der Client befindet, erreichen Sie Haltepunkte innerhalb des WCF-Dienstes.  
  
 Damit dies funktioniert, müssen Sie das Debuggen in der Datei app.config oder Web.config aktivieren. Informationen zum Aktivieren des Debuggens sowie Informationen zu Einschränkungen beim Ausführen von Einzelschritten in WCF-Dienste finden Sie unter [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>So führen Sie einen Einzelschritt in einen WCF-Dienst aus  
  
1. Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe, die sowohl den WCF-Client als auch WCF-Dienstprojekte enthält.  
  
2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das WCF-Clientprojekt, und klicken Sie dann auf **Als Startprojekt festlegen**.  
  
3. Aktivieren Sie das Debuggen in der Datei app.config oder web.config. Weitere Informationen finden Sie unter [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
4. Setzen Sie an der Stelle im Clientprojekt, an der Sie die schrittweise Ausführung beginnen möchten, einen Haltepunkt. Üblicherweise wird dies vor dem Aufruf des WCF-Diensts sein.  
  
5. Ausführen bis zum Haltepunkt, dann Beginnen der schrittweisen Ausführung. Der Debugger führt die schrittweise Ausführung des Diensts automatisch durch.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF-Debuggen](../debugger/limitations-on-wcf-debugging.md)   
 [Vorgehensweise: Debuggen eines lokal gehosteten WCF-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
