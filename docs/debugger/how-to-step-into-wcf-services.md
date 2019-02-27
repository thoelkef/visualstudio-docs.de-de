---
title: 'Vorgehensweise: Einzelschritts in WCF-Dienste | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fe025ed3050f25ec53175c543adfaf7cb48c506
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689810"
---
# <a name="how-to-step-into-wcf-services"></a>Gewusst wie: Ausführen eines Einzelschritts in WCF-Dienste
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie einen Einzelschritt in einen WCF-Dienst ausführen. Wenn sich der WCF-Dienst in derselben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe wie der Client befindet, erreichen Sie Haltepunkte innerhalb des WCF-Dienstes.

 Damit dies funktioniert, müssen Sie das Debuggen in der Datei app.config oder Web.config aktivieren. Informationen zum Aktivieren des Debuggens sowie Informationen zu Einschränkungen beim Ausführen von Einzelschritten in WCF-Dienste finden Sie unter [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>So führen Sie einen Einzelschritt in einen WCF-Dienst aus

1. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, die sowohl den WCF-Client als auch WCF-Dienstprojekte enthält.

2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das WCF-Clientprojekt, und klicken Sie dann auf **Als Startprojekt festlegen**.

3. Aktivieren Sie das Debuggen in der Datei app.config oder web.config. Weitere Informationen finden Sie unter [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).

4. Setzen Sie an der Stelle im Clientprojekt, an der Sie die schrittweise Ausführung beginnen möchten, einen Haltepunkt. Üblicherweise wird dies vor dem Aufruf des WCF-Diensts sein.

5. Ausführen bis zum Haltepunkt, dann Beginnen der schrittweisen Ausführung. Der Debugger führt die schrittweise Ausführung des Diensts automatisch durch.

## <a name="see-also"></a>Siehe auch
- [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)
- [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md)
- [Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)