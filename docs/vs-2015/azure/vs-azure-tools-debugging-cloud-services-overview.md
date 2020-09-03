---
title: Optionen zum Debuggen von Azure-Clouddiensten | Microsoft Docs
description: Debuggen von Azure-Clouddiensten
author: mikejo5000
manager: jillfra
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: df0322b26768ad5d325fc0fd07585f805fc96825
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919149"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Kennenlernen der verschiedenen Möglichkeiten zum Debuggen eines Azure-Clouddiensts
Dieser Artikel enthält Links zu verschiedenen Methoden zum Debuggen eines Azure-Clouddiensts. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Debuggen eines Azure-Clouddiensts in Visual Studio
Sie können Zeit und Geld sparen, wenn Sie den Azure-Compute-Emulator zum Debuggen Ihres Clouddiensts auf einem lokalen Computer verwenden. Durch lokales Debuggen eines Diensts vor der Bereitstellung können Sie die Zuverlässigkeit und Leistung verbessern, ohne für die Computezeit bezahlen zu müssen. Allerdings können einige Fehler nur auftreten, wenn Sie einen Clouddienst in Azure ausführen. Fehler, die nur beim Ausführen eines Clouddiensts in Azure auftreten, lassen sich debuggen, indem das Remotedebuggen beim Veröffentlichen des Diensts aktiviert und der Debugger dann an eine Rolleninstanz angefügt wird. Weitere Informationen finden Sie unter [Debuggen des Clouddiensts auf dem lokalen Computer](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Verwenden von IntelliTrace 
Wenn Sie Visual Studio Enterprise zum Schreiben von Rollen verwenden, die auf .NET Framework 4.5 ausgerichtet sind, können Sie IntelliTrace aktivieren, sobald Sie einen Clouddienst über Visual Studio bereitstellen. IntelliTrace bietet ein Protokoll, das Sie mit Visual Studio verwenden können, um die Anwendung so zu debuggen, als ob sie in Azure ausgeführt wird. Weitere Informationen finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

## <a name="remote-debugging"></a>Remotedebuggen 
Sie können das Remotedebuggen für Ihre Clouddienste zu dem Zeitpunkt aktivieren, zu dem Sie den Clouddienst über Visual Studio bereitstellen. Wenn Sie das Remotedebuggen für eine Bereitstellung aktivieren möchten, werden Dienste zum Remotedebuggen auf den virtuellen Computern installiert, auf denen jede Rolleninstanz ausgeführt wird. Diese Dienste, z.B. `msvsmon.exe`, haben keine Auswirkungen auf die Leistung und führen nicht zu zusätzlichen Kosten. Weitere Informationen finden Sie unter [Debuggen eines Clouddiensts in Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Nächste Schritte
- [Debuggen eines Azure-Clouddiensts oder virtuellen Computers in Visual Studio:](./vs-azure-tools-debug-cloud-services-virtual-machines.md) Erfahren Sie Näheres zum Debuggen von Azure-Clouddiensten.
