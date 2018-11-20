---
title: Optionen zum Debuggen von Azure-Clouddiensten | Microsoft-Dokumentation
description: Debuggen von Azure Cloud services
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001972"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Kennenlernen der verschiedenen Möglichkeiten zum Debuggen eines Azure-Clouddiensts
Dieser Artikel enthält Links zu den verschiedenen Möglichkeiten zum Debuggen von Azure-Clouddienst. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Debuggen eines Azure-Cloud-Diensts in Visual Studio
Sie können Zeit sparen und Geld sparen, mit dem Azure compute-Emulator zum Debuggen des Clouddiensts auf einem lokalen Computer. Durch lokales Debuggen eines Diensts, bevor Sie sie bereitstellen, können Sie die Zuverlässigkeit und Leistung verbessern, ohne dass Kosten für Compute-Zeit. Allerdings können einige Fehler auftreten, nur, wenn Sie einen Cloud-Dienst in Azure ausführen. Fehler, die auftreten, nur, wenn Sie einen Cloud-Dienst in Azure ausführen können durch Aktivieren von Remotedebuggen beim Veröffentlichen des Diensts, und klicken Sie dann das Anfügen des Debuggers zu einer Rolleninstanz gedebuggt werden. Weitere Informationen finden Sie unter [Debuggen des Clouddiensts auf dem lokalen Computer](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Verwenden von IntelliTrace 
Wenn Sie zum Schreiben, dass Rollen den .NET Framework 4.5 ausgerichtet sind. Visual Studio Enterprise verwenden, können Sie IntelliTrace zum Zeitpunkt aktivieren, dass Sie Azure-Clouddienst aus Visual Studio bereitstellen. IntelliTrace bietet ein Protokoll, das Sie mit Visual Studio verwenden können, um die Anwendung zu debuggen, als ob sie in Azure ausgeführt wurden. Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Remotedebuggen 
Sie können das Remotedebuggen auf Ihre Cloud-Dienste zum Zeitpunkt bei der Bereitstellung von Visual Studio Cloud-Dienst aktivieren. Wenn Sie das Remotedebuggen für eine Bereitstellung aktivieren möchten, werden remote Debuggen von Diensten auf den virtuellen Computern installiert, die jede Rolleninstanz ausgeführt. Diese Dienste, z. B. `msvsmon.exe` – nicht auf die Leistung auswirken oder zu zusätzlichen Kosten führen. Weitere Informationen finden Sie unter [Debuggen eines Clouddiensts in Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Nächste Schritte
- [Debuggen eines Azure-Clouddienst oder virtuellen Computer in Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) – ausführliche Informationen zum Debuggen von Azure Cloud Services.