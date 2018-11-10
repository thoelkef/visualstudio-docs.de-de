---
title: Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace | Microsoft-Dokumentation
description: Informationen Sie zum Debuggen eines Clouddiensts mit Visual Studio und IntelliTrace
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002011"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debuggen eines veröffentlichten Azure-Clouddiensts mit Visual Studio und IntelliTrace
Mit IntelliTrace können Sie umfangreiche Debuginformationen für eine Rolleninstanz protokollieren, wenn sie in Azure ausgeführt wird. Wenn Sie die Ursache eines Problems ermitteln möchten, können Sie die IntelliTrace-Protokolle, Ihren Code in Visual Studio schrittweise durchlaufen, als ob sie in Azure ausgeführt wurden. Zeichnet IntelliTrace Schlüssel aktiviert ist, Code und Umgebungsdaten bei die Azure-Anwendung als Cloud-Dienst in Azure ausgeführt wird, und Sie die Wiedergabe der aufgezeichneten Daten von Visual Studio können. 

Sie können IntelliTrace, wenn Sie Visual Studio Enterprise installiert haben und das Azure-Anwendung auf .NET Framework 4 oder höher. IntelliTrace sammelt Informationen für Ihre Azure-Rollen. Die virtuellen Computer für diese Rollen führen immer 64-Bit-Betriebssystemen.

Als Alternative können Sie [Remotedebuggen](http://go.microsoft.com/fwlink/p/?LinkId=623041) direkt an einen Cloud-Dienst angefügt werden soll, die in Azure ausgeführt wird.

> [!IMPORTANT]
> IntelliTrace ist nur für Debugszenarien bestimmt und sollte nicht für eine produktionsbereitstellung verwendet werden.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurieren einer Azure-Anwendung für IntelliTrace
Um IntelliTrace für eine Azure-Anwendung zu aktivieren, müssen Sie erstellen und veröffentlichen Sie die Anwendung aus einem Visual Studio-Azure-Projekt. Sie müssen IntelliTrace für Ihre Azure-Anwendung konfigurieren, bevor Sie ihn in Azure veröffentlichen. Wenn Sie Ihre Anwendung veröffentlichen, ohne IntelliTrace zu konfigurieren, müssen Sie das Projekt erneut veröffentlichen. Weitere Informationen finden Sie unter [Veröffentlichen einer Azure-Cloud services-Projekten, die mithilfe von Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Wenn Sie Ihre Azure-Anwendung bereitstellen möchten, stellen Sie sicher, dass die projektbuildziele, um festgelegt werden **Debuggen**.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste Projekt und wählen Sie im Kontextmenü des **veröffentlichen**.
   
1. In der **Azure-Anwendung veröffentlichen** Dialogfeld aus dem Azure-Abonnement, und wählen Sie **Weiter**.

1. In der **Einstellungen** Seite die **Erweiterte Einstellungen** Registerkarte.

1. Aktivieren Sie die **IntelliTrace aktivieren** Option aus, um die IntelliTrace-Protokolle für Ihre Anwendung zu sammeln, wenn sie in der Cloud veröffentlicht wird.
   
1. Wählen Sie zum Anpassen der IntelliTrace-Basiskonfiguration **Einstellungen** neben **IntelliTrace aktivieren**.

    ![Link für IntelliTrace-Einstellungen](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. In der **IntelliTrace-Einstellungen** Dialogfeld, Sie können angeben, welche Ereignisse Log, ob Aufrufinformationen erfasst werden sollen, welche Module und Prozesse zum Sammeln von Protokollen für, und wie viel Speicherplatz der Erfassung zugeordnet werden soll. Weitere Informationen zu IntelliTrace finden Sie unter [Debuggen mit IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![IntelliTrace-Einstellungen](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Das IntelliTrace-Protokoll ist eine zirkuläre Protokolldatei die maximale Größe in den IntelliTrace-Einstellungen (die Standardgröße beträgt 250 MB) angegeben. IntelliTrace-Protokolle werden in eine Datei im Dateisystem des virtuellen Computers gesammelt. Wenn Sie die Protokolle anfordern, wird eine Momentaufnahme ist zu diesem Zeitpunkt erstellt und auf dem lokalen Computer heruntergeladen.

Nach dem Azure-Clouddiensts in Azure veröffentlicht wurde, können Sie ermitteln, ob IntelliTrace vom Azure-Knoten in aktiviert wurde **Server-Explorer**, wie in der folgenden Abbildung gezeigt:

![Server-Explorer – IntelliTrace aktiviert](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Herunterladen von IntelliTrace-Protokolle für eine Rolleninstanz
Mithilfe von Visual Studio können Sie IntelliTrace-Protokolle für eine Rolleninstanz herunterladen, indem Sie diese Schritte:

1. In **Server-Explorer**, erweitern Sie die **Clouddienste** Knoten, und suchen Sie die Rolleninstanz, deren Protokolle, die Sie herunterladen möchten. 

1. Mit der rechten Maustaste der Rolleninstanz, und wählen Sie im Kontextmenü des s **IntelliTrace-Protokolle anzeigen**. 

    ![IntelliTrace-Protokolle anzeigen Menüoption](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Die IntelliTrace-Protokolle werden in einer Datei in einem Verzeichnis auf dem lokalen Computer heruntergeladen. Jedes Mal, dass die Anforderung der IntelliTrace-Protokolle, wird eine neue Momentaufnahme erstellt wird. Während die Protokolle heruntergeladen werden, handelt es sich bei Visual Studio zeigt den Fortschritt des Vorgangs in der **Azure Activity Log** Fenster. Wie in der folgenden Abbildung gezeigt, können Sie die Position für den Vorgang, um weitere Details finden Sie unter erweitern.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Sie können weiterhin in Visual Studio arbeiten, während die IntelliTrace-Protokolle heruntergeladen werden. Wenn das Protokoll vollständig heruntergeladen wurde, wird es in Visual Studio geöffnet.

> [!NOTE]
> Die IntelliTrace-Protokolle enthalten möglicherweise Ausnahmen, die vom Framework generierte und anschließend verarbeitet. Der interne Frameworkcode generiert diese Ausnahmen ganz normal im Rahmen des Starts einer Rolle, sodass Sie gefahrlos ignoriert werden können.
> 
> 

## <a name="next-steps"></a>Nächste Schritte
- [Optionen zum Debuggen von Azure-Cloud-Diensten](vs-azure-tools-debugging-cloud-services-overview.md)
- [Veröffentlichen von Azure-Clouddienst mit Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)