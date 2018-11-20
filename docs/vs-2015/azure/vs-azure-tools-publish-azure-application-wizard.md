---
title: Mithilfe des Visual Studio-Webpublishing-Assistenten der Azure-Anwendung | Microsoft-Dokumentation
description: Erfahren Sie, wie die verschiedenen Einstellungen in Visual Studio Veröffentlichen von Azure-Anwendung-Assistenten konfigurieren
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9c4104d4d07cab7486038a8787ed0c7759abd60
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002023"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Verwenden des Visual Studio-Assistenten für die Veröffentlichung von Azure-Anwendungen

Nachdem Sie eine Webanwendung in Visual Studio entwickelt haben, können Sie die Anwendung an einen Azure-Cloud-Dienst veröffentlichen, mit der **Azure-Anwendung veröffentlichen** Assistenten.

> [!Note]
> In diesem Artikel geht es bei Clouddiensten, nicht auf Websites bereitstellen. Informationen zum Bereitstellen von Websites finden Sie unter [Gewusst wie: Bereitstellen einer Azure-Website](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Zugreifen auf den Azure-Anwendung Veröffentlichen-Assistenten

Sie können den Azure-Anwendung Veröffentlichen-Assistenten auf zwei Arten je nach Art des Projekts von Visual Studio zugreifen, was man.

**Wenn Sie ein Azure-Cloud-Service-Projekt haben:**

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Projekts und wählen Sie im Kontextmenü des **veröffentlichen**.

**Wenn Sie ein Webanwendungsprojekt, die nicht für Azure aktiviert ist verfügen:**

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Projekts und wählen Sie im Kontextmenü des **konvertieren** > **in Azure Cloud-Dienstprojekt konvertieren**. 

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des neu erstellten Azure-Projekts und wählen Sie im Kontextmenü des **veröffentlichen**.

## <a name="sign-in-page"></a>Anmeldeseite

![Anmeldeseite](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Konto** – wählen Sie ein Konto, oder wählen Sie **Hinzufügen eines Kontos** in der Konto-Dropdownliste.

**Wählen Sie Ihr Abonnement** -wählen Sie das Abonnement für Ihre Bereitstellung verwenden.

## <a name="settings-page---common-settings-tab"></a>Seite "Einstellungen" – Registerkarte "Allgemeine Einstellungen"

![Allgemeine Einstellungen](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Cloud-Dienst** -verwenden die Dropdownliste, wählen Sie entweder einen vorhandenen Clouddienst aus, oder wählen  **&lt;neu erstellen >**, und erstellen Sie einen Cloud-Dienst. Das Datencenter wird für jeden Clouddienst in Klammern angezeigt. Es wird empfohlen, dass der Standort für den Clouddienst des Rechenzentrums als Datencenter-Speicherort für das Speicherkonto (Erweiterte Einstellungen) übereinstimmen.

**Umgebung** -wählen Sie entweder **Produktion** oder **Staging**. Wählen Sie die Stagingumgebung, wenn Sie Ihre Anwendung in einer testumgebung bereitstellen möchten. 

**Buildkonfiguration** -wählen Sie entweder **Debuggen** oder **Version**.

**Dienstkonfiguration** -wählen Sie entweder **Cloud** oder **lokalen**.

**Aktivieren Sie Remotedesktop für alle Rollen** -wählen Sie diese Option aus, wenn Sie Remote mit dem Dienst herstellen möchten. Diese Option wird in erster Linie für die Problembehandlung verwendet. Weitere Informationen finden Sie unter [Aktivieren einer Remotedesktopverbindung für eine Rolle in Azure Cloud Services mithilfe von Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Web Deploy für alle Webrollen aktivieren** -wählen Sie diese Option, um die webbereitstellung für den Dienst zu aktivieren. Sie müssen auch auswählen, die **Remotedesktop für alle Rollen aktivieren** Option aus, um dieses Feature zu verwenden. Weitere Informationen finden Sie unter [Veröffentlichen eines Clouddiensts mit Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Seite "Einstellungen" - Einstellungen-Registerkarte "Erweitert"

![Erweiterte Einstellungen](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Bezeichnung für die Bereitstellung** : übernehmen Sie den Standardnamen, oder geben Sie einen Namen Ihrer Wahl. Um der bereitstellungsbezeichnung das Datum anzufügen, lassen Sie das Kontrollkästchen aktiviert. 

**Storage-Konto** -wählen Sie das Speicherkonto für diese Bereitstellung verwenden **&lt;neu erstellen > um ein Speicherkonto zu erstellen. Das Datencenter wird für jedes Speicherkonto in Klammern angezeigt. Es wird empfohlen, dass Datencenter-Speicherort für das Speicherkonto an den Standort des Datencenters für den Cloud-Dienst (Erweiterte Einstellungen) identisch ist.

Azure-Speicherkonto speichert das Paket für die anwendungsbereitstellung. Nachdem die Anwendung bereitgestellt wurde, wird das Paket aus dem Speicherkonto entfernt.

**Bereitstellung bei Fehler löschen** -wählen Sie diese Option, um die Bereitstellung gelöscht, wenn während der Veröffentlichung Fehler auftreten. Dies sollte deaktiviert werden, wenn Sie eine Konstante virtuelle IP-Adresse für den Cloud-Dienst verwalten möchten.

**Bereitstellungsaktualisierung** -wählen Sie diese Option aus, wenn Sie nur aktualisierte Komponenten bereitstellen möchten. Diese Art der Bereitstellung kann schneller als eine vollständige Bereitstellung sein. Dies sollte überprüft werden, wenn Sie eine Konstante virtuelle IP-Adresse für den Cloud-Dienst verwalten möchten. 

**Bereitstellungsaktualisierung – Einstellungen** -dieses Dialogfeld wird verwendet, um festzulegen, wie Sie die Rollen aktualisiert werden sollen. Auf Wunsch **inkrementelles Update**, jede Instanz Ihrer Anwendung wird aktualisiert, nacheinander, damit die Anwendung immer verfügbar ist. Auf Wunsch **gleichzeitige Aktualisierung**, alle Instanzen der Anwendung werden gleichzeitig aktualisiert. Gleichzeitige Updates sind schneller, aber Ihr Dienst möglicherweise nicht zur Verfügung während des Updates.

![Bereitstellungseinstellungen](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Aktivieren von IntelliTrace** -angeben, wenn Sie IntelliTrace aktivieren möchten. Mit IntelliTrace können Sie umfangreiche Debuginformationen für eine Rolleninstanz protokollieren, wenn sie in Azure ausgeführt wird. Wenn Sie die Ursache eines Problems ermitteln möchten, können Sie die IntelliTrace-Protokolle, Ihren Code in Visual Studio schrittweise durchlaufen, als ob sie in Azure ausgeführt wurden. Weitere Informationen zum Verwenden von IntelliTrace finden Sie unter [Debuggen eines veröffentlichten Azure-Cloud-Diensts mit Visual Studio und IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Aktivieren der profilerstellung** -angeben, wenn Sie die Erstellung von Leistungsprofilen aktivieren möchten. Visual Studio-Profiler können Sie eine detaillierte Analyse der computingaspekte der Ausführung Ihres Clouddiensts zu erhalten. Weitere Informationen zur Verwendung von Visual Studio-Profiler finden Sie unter [Testen der Leistung von Azure-Clouddienst](./vs-azure-tools-performance-profiling-cloud-services.md).

**Remotedebugger für alle Rollen aktivieren** -angeben, wenn Sie das Remotedebuggen aktivieren möchten. Weitere Informationen zum Debuggen von Cloud Services mithilfe von Visual Studio finden Sie unter [Debuggen eines Azure-Clouddienst oder virtuellen Computer in Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Diagnostics-Seite "Einstellungen"

![Diagnoseeinstellungen](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnose können Sie eine Azure-Clouddienst (oder einen virtuellen Azure-Computer) zu behandeln. Weitere Informationen zur Diagnose finden Sie unter [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Weitere Informationen zu Application Insights finden Sie unter [Was ist Application Insights?](/azure/application-insights/app-insights-overview.md).

## <a name="summary-page"></a>Seite "Zusammenfassung"

![Zusammenfassung](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Zielprofil** – Sie können auch ein Veröffentlichungsprofil aus den Einstellungen zu erstellen, die Sie ausgewählt haben. Sie können beispielsweise ein Profil für eine testumgebung und eine für die Produktion erstellen. Um dieses Profil zu speichern, wählen die **speichern** Symbol. Der Assistent erstellt das Profil und speichert sie in Visual Studio-Projekt. Um den Namen des Profils zu ändern, öffnen die **Zielprofil** aus, und klicken Sie dann auf  **&lt;verwalten... &gt;**.

   > [!Note]
   > Das Veröffentlichungsprofil wird im Projektmappen-Explorer in Visual Studio angezeigt, und die profileinstellungen in eine Datei mit der Erweiterung ".azurepubxml" geschrieben werden. Einstellungen werden als Attribute des XML-Tags gespeichert.

## <a name="publishing-your-application"></a>Veröffentlichen der Anwendung

Wählen Sie nach dem Konfigurieren der Einstellungen für die Bereitstellung Ihres Projekts **veröffentlichen** am unteren Rand des Dialogfelds. Sie können den Prozessstatus im überwachen die **Ausgabe** Fenster in Visual Studio.

## <a name="next-steps"></a>Nächste Schritte

- [Migrieren und Veröffentlichen einer Webanwendung auf Azure-Clouddienst aus Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Erfahren Sie, wie Sie Visual Studio verwenden, um Azure-Clouddienst veröffentlichen](./vs-azure-tools-publishing-a-cloud-service.md)

- [Debuggen eines veröffentlichten Azure-Cloud-Diensts mit Visual Studio und IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Testen der Leistung von Azure-Clouddienst](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Was ist Application Insights?](/azure/application-insights/app-insights-overview.md)