---
title: Ausführen eines Einzelschritts in WCF-Diensten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 25ca1e4d2b7e0349ea5a41c6fc66726226ecab4f
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851891"
---
# <a name="how-to-step-into-wcf-services"></a>Vorgehensweise: Ausführen eines Einzelschritts in WCF-Diensten
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie einen Einzelschritt in einen WCF-Dienst ausführen. Wenn sich der WCF-Dienst in derselben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe wie der Client befindet, erreichen Sie Haltepunkte innerhalb des WCF-Dienstes.

 Damit dies funktioniert, müssen Sie das Debuggen in der Datei app.config oder Web.config aktivieren. Weitere Informationen zum Aktivieren des Debuggens sowie zu Einschränkungen beim Ausführen von Einzelschritten in WCF-Dienste finden Sie unter [Einschränkungen beim WCF-Debuggen](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>So führen Sie einen Einzelschritt in einen WCF-Dienst aus

1. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, die sowohl den WCF-Client als auch WCF-Dienstprojekte enthält.

2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das WCF-Clientprojekt, und klicken Sie dann auf **Als Startprojekt festlegen**.

3. Aktivieren Sie das Debuggen in der Datei app.config oder web.config. Weitere Informationen finden Sie unter [Einschränkungen beim WCF-Debuggen](../debugger/limitations-on-wcf-debugging.md).

4. Setzen Sie an der Stelle im Clientprojekt, an der Sie die schrittweise Ausführung beginnen möchten, einen Haltepunkt. Üblicherweise wird dies vor dem Aufruf des WCF-Diensts sein.

5. Ausführen bis zum Haltepunkt, dann Beginnen der schrittweisen Ausführung. Der Debugger führt die schrittweise Ausführung des Diensts automatisch durch.

## <a name="see-also"></a>Siehe auch
- [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)
- [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md)
- [How to: Debuggen eines lokal gehosteten WCF-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)