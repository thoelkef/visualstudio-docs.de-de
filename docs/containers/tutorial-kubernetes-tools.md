---
title: Tutorial zu Kubernetes-Tools | Microsoft-Dokumentation
ms.date: 06/08/2018
ms.topic: tutorial
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 7778019e73119a4b8b1a5842bb7a8c04ef017143
ms.sourcegitcommit: 50bbb62525c91c5a31bab57e1caf37c5638872c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87913304"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Erste Schritte mit Kubernetes-Tools in Visual Studio

Kubernetes-Tools in Visual Studio unterstützen die Optimierung der Entwicklung von Anwendungen in Containern für Kubernetes. Visual Studio kann die Dateien für die Konfiguration als Code automatisch erstellen, die für die Unterstützung der Kubernetes-Bereitstellung erforderlich sind, z. B. Dockerfiles und Helm-Charts. Sie können Ihren Code mithilfe von Azure Dev Spaces in einem aktiven AKS-Cluster (Azure Kubernetes Service) debuggen oder direkt innerhalb von Visual Studio in einem AKS-Cluster veröffentlichen.

In diesem Tutorial wird die Verwendung von Visual Studio zum Hinzufügen von Kubernetes-Unterstützung zu einem Projekt und für die Veröffentlichung in AKS behandelt. Wenn Sie hauptsächlich daran interessiert sind, [Azure Dev Spaces](/azure/dev-spaces/) zum Debuggen und Testen Ihres Projekts in AKS zu verwenden, können Sie stattdessen mit dem [Azure Dev Spaces-Tutorial](/azure/dev-spaces/get-started-netcore-visualstudio) fortfahren.

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen Folgendes, um diese neue Funktionalität zu nutzen:

::: moniker range="vs-2017"
- Die neueste Version von [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit der Workload *ASP.NET und Webentwicklung*.
- Das [Kubernetes-Tool für Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), das als separater Download verfügbar ist.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit der Workload *ASP.NET- und Webentwicklung*
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) auf Ihrer Entwicklungsarbeitsstation installiert (d. h. der Computer, auf dem Sie Visual Studio ausführen), wenn Sie Docker-Images erstellen, lokal ausgeführte Docker-Container debuggen oder in AKS veröffentlichen möchten. (Docker ist für das Erstellen und Debuggen von Docker-Containern in AKS mithilfe von Azure Dev Spaces *nicht* erforderlich.)
::: moniker range="vs-2017"
- Wenn Sie über Visual Studio in AKS veröffentlichen möchten (*nicht* für das Debuggen in AKS mithilfe von Azure Dev Spaces erforderlich):

    1. Die [AKS-Veröffentlichungstools](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), die als separater Download verfügbar sind.

    1. Ein Azure Kubernetes Service-Cluster. Weitere Informationen finden Sie unter [Erstellen eines AKS-Clusters](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Stellen Sie sicher, dass Sie über Ihre Entwicklungsarbeitsstation [eine Verbindung mit dem Cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) herstellen.

    1. Die Helm-Befehlszeilenschnittstelle muss auf Ihrer Entwicklungsarbeitsstation installiert sein. Weitere Informationen finden Sie unter [Installieren von Helm](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Helm muss mithilfe des `helm init`-Befehls für Ihren AKS-Cluster konfiguriert sein. Weitere Informationen hierzu finden Sie unter [Konfigurieren von Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Erstellen eines neuen Kubernetes-Projekts

::: moniker range="vs-2017"

Sobald Sie die entsprechenden Tools installiert haben, starten Sie Visual Studio, und erstellen Sie ein neues Projekt. Wählen Sie unter **Cloud** den Projekttyp **Containeranwendung für Kubernetes** aus. Wählen Sie den Projekttyp aus, und klicken Sie auf **OK**.

![Screenshot: Erstellen eines neuen Kubernetes-App-Projekts](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Suchen Sie im Visual Studio-Startfenster nach *Kubernetes*, und wählen Sie dann **Containeranwendung für Kubernetes** aus.

![Screenshot: Erstellen eines neuen Kubernetes-App-Projekts](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Geben Sie den Projektnamen an.

![Screenshot: Erstellen eines neuen Kubernetes-App-Projekts](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Anschließend können Sie auswählen, welche Art von ASP.NET Core-Webanwendung erstellt werden soll. Wählen Sie eine **Webanwendung** aus. Die übliche Option **Docker-Unterstützung aktivieren** wird in diesem Dialogfeld nicht angezeigt.  Die Docker-Unterstützung ist für Containeranwendungen in Kubernetes standardmäßig aktiviert.

::: moniker range="vs-2017"

![Screenshot: Auswahl der Option „Webanwendung“](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot: Auswahl der Option „Webanwendung“](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Hinzufügen von Kubernetes-Unterstützung zu einem vorhandenen Projekt

Alternativ können Sie Kubernetes-Unterstützung zu einem vorhandenen ASP.NET Core-Webanwendungsprojekt hinzufügen. Klicken Sie hierzu mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Hinzufügen** > **Unterstützung für Containerorchestrator** aus.

::: moniker range="vs-2017"

![Screenshot: Menüelement zum Hinzufügen von Containerorchestratoren](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot: Menüelement zum Hinzufügen von Containerorchestratoren](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

Wählen Sie im Dialogfeld die Option **Kubernetes/Helm** aus, und klicken Sie dann auf **OK**.

![Screenshot: Dialogfeld zum Hinzufügen von Containerorchestratoren](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Was Visual Studio für Sie erstellt

Nachdem Sie ein neues Projekt vom Typ **Containeranwendung für Kubernetes** erstellt oder die Unterstützung von Kubernetes-Containerorchestratoren zu einem vorhandenen Projekt hinzugefügt haben, befinden sich einige zusätzliche Dateien in Ihrem Projekt, die die Bereitstellung in Kubernetes unterstützen.

::: moniker range="vs-2017"

![Screenshot: Projektmappen-Explorer nach Hinzufügen der Containerorchestratorunterstützung](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Screenshot: Projektmappen-Explorer nach Hinzufügen der Containerorchestratorunterstützung](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Die folgenden Dateien wurden hinzugefügt:

- Eine Dockerfile, die Ihnen das Generieren eines Docker-Containerimages ermöglicht, das die Webanwendung hostet. Sie werden sehen, dass die Visual Studio-Tools diese Dockerfile beim Debuggen und Bereitstellen in Kubernetes nutzen. Wenn Sie die direkte Arbeit mit dem Docker-Image bevorzugen, können Sie mit der rechten Maustaste auf die Dockerfile klicken und dann **Docker-Image erstellen** auswählen.

   ![Screenshot: Option „Docker-Image erstellen“](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Ein Helm-Chart und ein *Charts*-Ordner. Diese YAML-Dateien bilden das Helm-Chart für die Anwendung, die Sie für die Bereitstellung in Kubernetes verwenden können. Weitere Informationen zu Helm finden Sie unter [https://www.helm.sh](https://www.helm.sh).

- *azds.yaml*. Diese Datei enthält Einstellungen für Azure Dev Spaces, was eine schnelle, iterative Debugfunktion in Azure Kubernetes Service bereitstellt. Weitere Informationen finden Sie in der [Dokumentation zu Azure Dev Spaces](/azure/dev-spaces/azure-dev-spaces).

:::moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Veröffentlichen in Azure Kubernetes Service (AKS)

Wenn all diese Dateien vorhanden sind, können Sie die Visual Studio-IDE verwenden, um Ihren Anwendungscode wie gewohnt zu schreiben und zu debuggen. Sie können [Azure Dev Spaces](/azure/dev-spaces/) auch verwenden, um Ihren Code schnell auszuführen und zu debuggen, während er in einem AKS-Cluster ausgeführt wird. Weitere Informationen finden Sie im [Azure Dev Spaces-Tutorial](/azure/dev-spaces/get-started-netcore-visualstudio).

Sobald ihr Code wie gewünscht ausgeführt wird, können Sie die Veröffentlichung in einem AKS-Cluster direkt über Visual Studio ausführen.

Hierzu müssen Sie zunächst überprüfen, ob Sie alles gemäß des Punkts zur Veröffentlichung in AKS im Abschnitt [Voraussetzungen](#prerequisites) installiert und alle Befehlszeilenschritte unter den Links ausgeführt haben. Anschließend richten Sie ein Veröffentlichungsprofil ein, mit dem Ihr Containerimage in ACR (Azure Container Registry) veröffentlicht wird. Anschließend kann AKS Ihr Containerimage per Pull aus ACR abrufen und im Cluster bereitstellen.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Ihr *Projekt*, und wählen Sie dann **Veröffentlichen** aus.

   ![Screenshot: Menüelement „Veröffentlichen“](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Wählen Sie auf der Anzeige **Veröffentlichen** die Option **Container Registry** als Veröffentlichungsziel aus, und befolgen Sie die Anweisungen, um Ihre Containerregistrierung auszuwählen. Wenn Sie über keine Containerregistrierung verfügen, klicken Sie auf **Neue Azure Container Registry-Instanz erstellen**, um eine Containerregistrierung über Visual Studio zu erstellen. Weitere Informationen finden Sie unter [Veröffentlichen Ihres Containers in Azure Container Registry](hosting-web-apps-in-docker.md).

   ![Screenshot: Anzeige zum Auswählen eines Veröffentlichungsziels](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihre *Projektmappe*, und wählen Sie dann **Publish to Azure AKS** (In Azure Kubernetes Service veröffentlichen) aus.

   ![Screenshot: Menüelement „Publish to Azure AKS“ (In Azure Kubernetes Service veröffentlichen)](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Wählen Sie Ihr Abonnement und Ihren AKS-Cluster sowie das ACR-Veröffentlichungsprofil aus, das Sie soeben erstellt haben. Klicken Sie dann auf **OK**.

   ![Screenshot: Anzeige „Publish to AKS“ (In AKS veröffentlichen)](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Dadurch gelangen Sie zur Anzeige **Publish to Azure AKS** (In Azure Kubernetes Service veröffentlichen).

5. Klicken Sie auf den Link **Configure Helm** (Helm konfigurieren), um die verwendete Befehlszeile zu ändern, die zum Installieren der Helm-Charts auf dem Server verwendet wird.

   ![Screenshot: Link „Configure Helm“ (Helm konfigurieren)](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Das Ändern der Befehlszeile ist nützlich, wenn Sie benutzerdefinierte Befehlszeilenargumente festlegen möchten, z. B. einen anderen Namen für Kubernetes-Kontexte oder -Charts.

   ![Screenshot: Anzeige „Helm konfigurieren“](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Wenn Sie bereit für die Bereitstellung sind, klicken Sie auf **Veröffentlichen**, um Ihre Anwendung in AKS zu veröffentlichen.

   ![Screenshot: Anzeige für die Veröffentlichung in AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Herzlichen Glückwunsch! Sie können jetzt das gesamte Potenzial von Visual Studio für Ihre Kubernetes-App-Entwicklung nutzen.

## <a name="remove-kubernetes-support"></a>Entfernen der Kubernetes-Unterstützung

1. Öffnen Sie im **Projektmappen-Explorer** unter **Eigenschaften** die Datei *launchSettings.json*.

1. Löschen Sie den Abschnitt **Container in Kubernetes**.

1. Wählen Sie, wenn Sie zu Docker Compose zurückkehren, dieses Projekt im **Projektmappen-Explorer** aus. Klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Als Startprojekt festlegen**.

1. (Optional) Sie können auch andere Artefakte löschen, die wie oben in diesem Artikel erwähnt aufgeführt sind, wie z. B. den Ordner **charts** und die Datei *azds.yaml*.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über die Kubernetes-Entwicklung in Azure finden Sie in der [Dokumentation zu Azure Kubernetes Service](/azure/aks).

Weitere Informationen über Azure Dev Spaces finden Sie in [Dokumentation zu Azure Dev Spaces](/azure/dev-spaces/).
