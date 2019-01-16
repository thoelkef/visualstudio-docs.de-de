---
title: Tutorial für Kubernetes-Tools | Microsoft-Dokumentation
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 8cb250cd319f28b444a8f3bfecef421ecbaac9b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848362"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Erste Schritte mit Kubernetes-Tools für Visual Studio

Die Visual Studio-Kubernetes-Tools vereinfachen die Entwicklung von Anwendungen in Containern für Kubernetes. Visual Studio kann die Konfiguration als Code erforderlichen Dateien für Kubernetes-Bereitstellung, z. B. dockerfile-Dateien und Helm-Diagrammen unterstützen automatisch erstellen. Sie können Debuggen Ihres Codes in einem aktiven Azure Kubernetes Service (AKS)-Cluster mithilfe von Azure-Dev-Speicherplätzen oder direkt in einem AKS-Cluster aus veröffentlichen in Visual Studio.

In diesem Tutorial wird die Verwendung von Visual Studio zum Hinzufügen von Kubernetes-Unterstützung zu einem Projekt, und Veröffentlichen in AKS behandelt. Wenn Sie in erster Linie mit [Azure Dev Leerzeichen](http://aka.ms/get-azds) zum Debuggen und Testen Sie das Projekt, das in AKS ausgeführte, können Sie direkt zum die [Tutorial für Azure Dev Leerzeichen](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio) stattdessen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um diese neue Funktionalität nutzen zu können, benötigen Sie Folgendes:

- Die neueste Version des [Visual Studio 2017](https://visualstudio.microsoft.com/download) mit der *ASP.NET und Webentwicklung* arbeitsauslastung.

- Die [Kubernetes-Tools für Visual Studio](https://aka.ms/get-vsk8stools), als separater Download zur Verfügung.

- [Docker für Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows) auf Ihrer Entwicklungsarbeitsstation installiert (d. h., in denen Sie Visual Studio ausführen), wenn Sie Docker-Images erstellen möchten, lokal ausgeführte Docker-Containern zu debuggen oder Veröffentlichen von AKS. (Docker *nicht* zum Entwickeln und Debuggen von Docker-Container in AKS über Azure Dev Leerzeichen erforderlich.)

- Wenn Sie in AKS von Visual Studio aus veröffentlichen möchten (*nicht* für das Debuggen in AKS über Azure Dev Leerzeichen erforderlich):

    1.  Die [AKS-Tools für die Veröffentlichung](https://aka.ms/get-vsk8spublish), als separater Download zur Verfügung.

    1.  Ein Azure Kubernetes Service-Cluster. Weitere Informationen finden Sie unter [zum Erstellen eines AKS-Clusters](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). Achten Sie darauf, um [Verbinden mit dem Cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) von Ihrer Entwicklungsarbeitsstation.

    1.  Helm-CLI auf Ihrer Entwicklungsarbeitsstation installiert. Weitere Informationen finden Sie unter [Installieren von Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  Helm in Ihrem AKS-Cluster konfiguriert werden, mithilfe der `helm init` Befehl. Weitere Informationen zu dieser Vorgehensweise finden Sie unter [Vorgehensweise: Konfigurieren von Helm](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Erstellen eines neuen Projekts für Kubernetes

Nachdem Sie die entsprechenden Tools installiert haben, starten Sie Visual Studio, und Erstellen eines neuen Projekts. Klicken Sie unter **Cloud**, wählen Sie die **Containeranwendung für Kubernetes** Projekttyp. Wählen Sie diesen Projekttyp und **OK**.

![Screenshot: erstellen ein neues Projekt des Kubernetes-app](media/k8s-tools-new-k8s-app.png)

Sie können dann der von ASP.NET Core-Webanwendung erstellen auswählen. Wählen Sie **Webanwendung** , und wählen Sie **OK**. Die üblichen **Docker-Unterstützung aktivieren** Option wird in diesem Dialogfeld nicht angezeigt.  Docker-Unterstützung ist standardmäßig für einer containeranwendung für Kubernetes aktiviert.

![Screenshot der Auswahl der Web-app](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Kubernetes-Unterstützung zu einem vorhandenen Projekt hinzufügen

Alternativ können Sie einen Kubernetes-Unterstützung zu einem vorhandenen ASP.NET Core Web Application-Projekt hinzufügen. Zu diesem Zweck mit der rechten Maustaste auf das Projekt, und wählen **hinzufügen** > **Unterstützung für Containerorchestrator**.

![Screenshot des hinzufügen Containerorchestrator-Menüelement](media/k8s-tools-add-container-orchestrator.png)

Klicken Sie im Dialogfeld "Kubernetes/Helm" auswählen, und wählen Sie **OK**.

![Screenshot des hinzufügen Containerorchestrator (Dialogfeld)](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Was Visual Studio für Sie erstellt

Nach dem Erstellen eines neuen **Containeranwendung für Kubernetes** Projekt oder die Unterstützung für containerorchestrator Kubernetes zu einem vorhandenen Projekt hinzufügen, werden Sie sehen einige zusätzlichen Dateien in Ihrem Projekt, das Bereitstellen in Kubernetes.

![Screenshot des Projektmappen-Explorer nach dem Hinzufügen von Unterstützung für Containerorchestrator](media/k8s-tools-solution-explorer.png)

Die hinzugefügten Dateien sind:

- eine dockerfile-Datei zum Generieren von Docker Container-Images, die dieser Webanwendung hosten kann. Wie Sie sehen werden, nutzt die Visual Studio-Tools dieser dockerfile-Datei beim Debuggen und Bereitstellen in Kubernetes. Wenn Sie direkt mit der Docker-Image zu arbeiten lieber, können Sie mit der rechten Maustaste auf die dockerfile-Datei und wählen Sie **Docker-Image erstellen**.

   ![Screenshot des erstellen Sie Docker-Image-option](media/k8s-tools-build-docker-image.png)

- ein Helm-Diagramm und eine *Diagramme* Ordner. Diese Yaml-Dateien bilden zusammen das Helm-Diagramm für die Anwendung, die Sie verwenden können, um in Kubernetes bereitgestellt. Weitere Informationen zum Helm, finden Sie unter [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Enthält Einstellungen für Azure Dev Leerzeichen, die eine schnelle, iterative Debugleistung in Azure Kubernetes Service bereitstellt. Weitere Informationen finden Sie [der Dokumentation zu Azure Dev Leerzeichen](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

## <a name="publish-to-azure-kubernetes-service-aks"></a>Veröffentlichen Sie in Azure Kubernetes Service (AKS)

Mit diesen Dateien vorhanden können Sie Visual Studio-IDE schreiben und Debuggen von Ihrem Anwendungscode verwenden, so wie bisher. Sie können auch [Azure Dev Leerzeichen](http://aka.ms/get-azds) schnell ausführen und Debuggen Ihres Codes in einem AKS-Cluster live ausgeführt. Weitere Informationen finden Sie die [Speicherplätze für Azure-Dev-Tutorial](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)

Sobald Sie Ihr Code ausgeführt werden sollen haben, wie Sie können direkt aus Visual Studio in einem AKS-Cluster veröffentlichen.

Zu diesem Zweck müssen Sie zuerst überprüfen Sie, dass Sie alles, was installiert haben, siehe die [Voraussetzungen](#prerequisites) Abschnitt unter dem Element, für die Veröffentlichung in AKS, und führen Sie alle angegebenen Links über die Befehlszeile Schritten. Dann richten Sie ein Veröffentlichungsprofil, das Ihr containerimage auf der Azure Container Registry (ACR) veröffentlicht. Anschließend können AKS pull des containerimages von ACR und ihn in den Cluster bereitstellen.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste auf Ihre *Projekt* , und wählen Sie **veröffentlichen**.

   ![Screenshot der veröffentlichen-Menüelement](media/k8s-tools-publish-project.png)

2. In der **veröffentlichen** Bildschirm **Containerregistrierung** als Veröffentlichungsziel, und führen Sie die aufforderungen, um Ihre containerregistrierung zu wählen. Wenn Sie nicht bereits eine containerregistrierung haben, wählen Sie **erstellen Sie neue Azure Container Registry** aus Visual Studio erstellen. Weitere Informationen finden Sie unter [veröffentlichen Sie Ihre Container in Azure Container Registry](#publish-your-container-to-azure-container-registry).

   ![Screenshot der Kommissionierung ein Zielbildschirm veröffentlichen](media/k8s-tools-publish-to-acr.png)

3. Zurück im Projektmappen-Explorer, klicken Sie mit der rechten Maustaste auf Ihre *Lösung* , und klicken Sie auf **Veröffentlichen in Azure AKS**.

   ![Screenshot der in Azure AKS-Menüelement zu veröffentlichen](media/k8s-tools-publish-solution.png)

4. Wählen Sie Ihr Abonnement und in Ihrem AKS-Cluster, zusammen mit den ACR Veröffentlichungsprofil, das Sie gerade erstellt haben. Klicken Sie dann auf **OK**.

   ![Screenshot des AKS-Bildschirm zu veröffentlichen](media/k8s-tools-publish-to-aks.png)

   Dadurch gelangen Sie auf die **Veröffentlichen in Azure AKS** Bildschirm.

5. Wählen Sie die **konfigurieren Helm** Link, um die Befehlszeile zum Installieren von Helm-Diagramme auf dem Server zu aktualisieren.

   ![Screenshot der Konfigurieren von Helm-link](media/k8s-tools-configure-helm.png)

   Aktualisieren die Befehlszeile ist hilfreich, wenn benutzerdefinierte Befehlszeilenargumente, die Sie, wie z. B. einen anderen Namen von Kubernetes-Kontext oder ein Diagramm angeben möchten.

   ![Screenshot der von Helm konfigurieren Bildschirm](media/k8s-tools-helm-configure-screen.png)

6. Wenn Sie bereitstellen möchten, klicken Sie auf die **veröffentlichen** Schaltfläche zum Veröffentlichen der Anwendung in AKS.

   ![Screenshot der in Azure AKS-Bildschirm veröffentlichen](media/k8s-tools-publish-screen.png)

Herzlichen Glückwunsch! Sie können jetzt die volle Leistungsfähigkeit von Visual Studio für alle Ihre Kubernetes-app-Entwicklung verwenden.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Kubernetes-Entwicklung in Azure durch Lesen der [Dokumentation AKS](/azure/aks).

Erfahren Sie mehr über Azure Dev Leerzeichen durch Lesen der [Speicherplätze für Azure-Dev-Dokumentation](http://aka.ms/get-azds)
