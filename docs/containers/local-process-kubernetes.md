---
title: Verwenden des lokalen Prozesses mit Kubernetes und Visual Studio
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Hier erfahren Sie, wie Sie den lokalen Prozess mit Kubernetes und Visual Studio verwenden, um Ihren Entwicklungscomputer mit einem Kubernetes-Cluster zu verbinden.
keywords: Lokaler Prozess mit Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, Container
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 62b07affd1e54b0dfa8127ecf57626e90ed7dd0e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037444"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Verwenden des lokalen Prozesses mit Kubernetes (Vorschau)

Der lokale Prozess mit Kubernetes ermöglicht Ihnen das Ausführen und Debuggen von Code auf Ihrem Entwicklungscomputer, während der Kubernetes-Cluster weiterhin mit den übrigen Anwendungen oder Diensten verbunden ist. Wenn Sie z. B. über eine umfangreiche Microservicearchitektur mit einer Vielzahl von Diensten und Datenbanken verfügen, die voneinander abhängig sind, kann es schwierig sein, diese Abhängigkeiten auf Ihrem Entwicklungscomputer zu replizieren. Außerdem kann der Vorgang zum Erstellen und Bereitstellen von Code in Ihrem Kubernetes-Cluster für jede Codeänderung während der Inner Loop-Entwicklung langsam, zeitaufwendig und bei Verwendung mit einem Debugger wenig benutzerfreundlich sein.

Bei Verwendung des lokalen Prozesses mit Kubernetes muss Ihr Code nicht erstellt und im Cluster bereitgestellt werden. Stattdessen wird eine direkte Verbindung zwischen Ihrem Entwicklungscomputer und Ihrem Cluster hergestellt. Indem Sie Ihren Entwicklungscomputer während des Debuggens mit Ihrem Cluster verbinden, können Sie Ihren Dienst im Handumdrehen im Kontext der gesamten Anwendung testen und entwickeln, ohne dazu eine Docker- oder Kubernetes-Konfiguration erstellen zu müssen.

Wenn Sie den lokalen Prozess mit Kubernetes verwenden, wird Datenverkehr zwischen Ihrem verbundenen Kubernetes-Cluster und Ihrem Entwicklungscomputer umgeleitet. Diese Umleitung des Datenverkehrs ermöglicht es, dass Code auf dem Entwicklungscomputer und die im Kubernetes-Cluster ausgeführten Dienste so kommunizieren, als befänden sie sich im gleichen Kubernetes-Cluster. Der lokale Prozess bietet außerdem die Möglichkeit, die für Pods im Kubernetes-Cluster verfügbaren Umgebungsvariablen und bereitgestellten Volumes auf dem Entwicklungscomputer zu replizieren. Indem Sie auf Ihrem Entwicklungscomputer auf Umgebungsvariablen und bereitgestellte Volumes zugreifen können, können Sie Ihren Code rasch bearbeiten, ohne diese Abhängigkeiten manuell replizieren zu müssen.

In dieser Anleitung erfahren Sie, wie Sie den lokalen Prozess mit Kubernetes nutzen, um Datenverkehr zwischen Ihrem Kubernetes-Cluster und ausgeführtem Code auf Ihrem Entwicklungscomputer umzuleiten. Darüber hinaus finden Sie in dieser Anleitung ein Skript zur Bereitstellung einer umfangreichen Beispielanwendung mit mehreren Microservices auf einem Kubernetes-Cluster.

> [!IMPORTANT]
> Diese Funktion steht derzeit als Vorschau zur Verfügung. Vorschauversionen werden Ihnen zur Verfügung gestellt, wenn Sie die [zusätzlichen Nutzungsbedingungen][preview-terms] akzeptieren. Einige Aspekte dieses Features werden bis zur allgemeinen Verfügbarkeit unter Umständen noch geändert.

## <a name="before-you-begin"></a>Voraussetzungen

In dieser Anleitung wird die [Azure Dev Spaces-Beispielanwendung „Bike Sharing“][bike-sharing-github] verwendet, um zu veranschaulichen, wie Sie Ihren Entwicklungscomputer mit einem Kubernetes-Cluster verbinden. Wenn Sie bereits über eine eigene Anwendung in einem Kubernetes-Cluster verfügen, können Sie die folgenden Schritte dennoch ausführen und dabei die Namen Ihrer eigenen Dienste verwenden.

### <a name="prerequisites"></a>Voraussetzungen

* Ein Azure-Abonnement. Falls Sie über kein Azure-Abonnement verfügen, können Sie ein [kostenloses Konto](https://azure.microsoft.com/free) erstellen.
* Die [Azure CLI][azure-cli] muss installiert sein.
* Mindestens die [Visual Studio 2019][visual-studio]-Version 16.7 Preview 4 muss installiert sein und unter Windows 10 mit der Workload *Azure-Entwicklung* ausgeführt werden.
* [Die Erweiterung für lokale Prozesse für Kubernetes muss installiert sein][lpk-extension].

Installieren Sie für .NET-Konsolenanwendungen außerdem das NuGet-Paket *Microsoft.VisualStudio.Azure.Kubernetes.Tools.Targets*.

## <a name="create-a-kubernetes-cluster"></a>Erstellen eines Kubernetes-Clusters

Erstellen Sie einen AKS-Cluster in einer [unterstützten Region][supported-regions]. Mit den unten angegebenen Befehlen wird eine Ressourcengruppe mit dem Namen *MyResourceGroup* und der AKS-Cluster *MyAKS* erstellt.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Installieren der Beispielanwendung

Installieren Sie die Beispielanwendung mithilfe des bereitgestellten Skripts auf Ihrem Cluster. Sie können das Skript auch mithilfe von [ Azure Cloud Shell][azure-cloud-shell] ausführen.

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

Navigieren Sie zur Beispielanwendung auf Ihrem Cluster, indem Sie die öffentliche URL aufrufen, die in der Ausgabe des Installationsskripts angezeigt wird.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

Im obigen Beispiel lautet die öffentliche URL `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Herstellen einer Clusterverbindung und Debuggen eines Diensts

Laden Sie auf dem Entwicklungscomputer die Kubernetes-CLI herunter, und konfigurieren Sie sie, um unter Verwendung von [az aks get-credentials][az-aks-get-credentials] eine Verbindung mit Ihrem Kubernetes-Cluster herzustellen.

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

Öffnen Sie in Visual Studio in der [Azure Dev Spaces-Beispielanwendung „Bike Sharing“][bike-sharing-github] den Pfad *mindaro/samples/BikeSharingApp/ReservationEngine/app.csproj*.

Wählen Sie in Ihrem Projekt wie nachfolgend gezeigt im Dropdownmenü mit den Starteinstellungen die Option *Lokaler Prozess mit Kubernetes* aus.

![Auswählen des lokalen Prozesses mit Kubernetes](media/local-process-kubernetes/choose-local-process.png)

Klicken Sie auf die Startschaltfläche neben *Lokaler Prozess mit Kubernetes*. Führen Sie im Dialogfeld *Lokaler Prozess mit Kubernetes* folgende Schritte aus:

* Wählen Sie Ihr Abonnement aus.
* Wählen Sie *MyAKS* als Cluster aus.
* Wählen Sie *dev* als Namespace aus.
* Wählen Sie *reservationengine* als Dienst für die Umleitung aus.
* Wählen Sie *app* als Startprofil aus.
* Wählen Sie `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` als URL zum Starten Ihres Browsers aus.

![Auswählen des lokalen Prozesses mit Kubernetes-Cluster](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> Sie können nur Dienste umleiten, die über einen einzelnen Pod verfügen.

Klicken Sie auf *Speichern und Debuggen starten*.

Der gesamte Datenverkehr im Kubernetes-Cluster wird für den Dienst *reservationengine* an die Version der Anwendung umgeleitet, die auf dem Entwicklungscomputer ausgeführt wird. Der lokale Prozess mit Kubernetes leitet zudem den gesamten ausgehenden Datenverkehr der Anwendung zurück an den Kubernetes-Cluster.

> [!NOTE]
> Sie werden aufgefordert, die Ausführung von *KubernetesDNSManager* mit erhöhten Rechten zuzulassen und zu erlauben, dass Ihre Hostdatei geändert wird.

Sobald in der Statusleiste angezeigt wird, dass Sie mit dem *reservationengine*-Dienst verbunden sind, ist Ihr Entwicklungscomputer verbunden.

![Verbundener Entwicklungscomputer](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> Bei nachfolgenden Startvorgängen wird das Dialogfeld *Lokaler Prozess mit Kubernetes* nicht erneut angezeigt. Diese Einstellungen werden in den Projekteigenschaften im Bereich *Debuggen* aktualisiert.

Sobald Ihr Entwicklungscomputer verbunden ist, wird Datenverkehr für den Dienst, den Sie ersetzen, an den Entwicklungscomputer umgeleitet.

## <a name="set-a-break-point"></a>Festlegen eines Haltepunkts

Öffnen Sie [BikesHelper.cs][bikeshelper-cs-breakpoint], und klicken Sie auf Zeile 26, um den Cursor dort zu platzieren. Drücken Sie zum Festlegen eines Haltepunkts die Taste *F9*, oder klicken Sie auf *Debuggen* und dann auf *Haltepunkt umschalten*.

Rufen Sie die öffentliche URL auf, um zur Beispielanwendung zu navigieren. Wählen Sie *Aurelia Briggs (customer)* als Benutzer und dann ein zu mietendes Fahrrad aus. Klicken Sie auf *Rent Bike* (Fahrrad mieten). Wechseln Sie zurück zu Visual Studio. Sie sehen, dass Zeile 26 hervorgehoben ist. Durch den festgelegten Haltepunkt wurde der Dienst in Zeile 26 angehalten. Drücken Sie zum Fortsetzen des Diensts *F5*, oder klicken Sie auf *Debuggen* und dann auf *Weiter*. Wechseln Sie erneut in Ihren Browser, und überprüfen Sie, ob auf der Seite angezeigt wird, dass Sie das Fahrrad gemietet haben.

Entfernen Sie den Haltepunkt, indem Sie den Cursor in `BikesHelper.cs` in Zeile 26 platzieren und *F9* drücken.

> [!NOTE]
> Wenn Sie den Debugtask anhalten, wird standardmäßig auch Ihr Entwicklungscomputer vom Kubernetes-Cluster getrennt. Sie können dieses Verhalten ändern, indem Sie im Abschnitt *Kubernetes-Debugtools* in den Debugoptionen die Einstellung *Verbindung nach dem Debuggen trennen* auf *false* festlegen. Wenn Sie diese Einstellung geändert haben, bleibt Ihr Entwicklungscomputer verbunden, wenn Sie das Debuggen beenden und starten. Zum Trennen Ihres Entwicklungscomputers vom Cluster klicken Sie in der Symbolleiste auf die Schaltfläche *Trennen*.
>
> Wenn Visual Studio die Verbindung mit dem Cluster abrupt beendet, wird der Dienst, für den Sie die Umleitung vornehmen, möglicherweise nicht im ursprünglichen Zustand wiederhergestellt, bevor die Verbindung mit dem lokalen Prozess mit Kubernetes hergestellt wurde. Informationen zum Beheben dieses Problems finden Sie in den Anleitungen zur [Problembehandlung][troubleshooting].

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Der lokale Prozess mit Kubernetes kann die Weiterleitung des Datenverkehrs und die Replikation von Umgebungsvariablen ohne weitere Konfiguration verarbeiten. Wenn Sie Dateien herunterladen müssen, die in den Container im Kubernetes-Cluster eingebunden sind, z. B. eine ConfigMap-Datei, können Sie eine `KubernetesLocalProcessConfig.yaml`-Datei erstellen, um diese Dateien auf den Entwicklungscomputer herunterzuladen. Weitere Informationen finden Sie unter [Verwenden von KubernetesLocalProcessConfig.yaml zur zusätzlichen Konfiguration für den lokalen Prozess mit Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Verwenden der Protokollierung und Diagnose

Sie finden die Diagnoseprotokolle auf dem Entwicklungscomputer im Verzeichnis `Local Process with Kubernetes` im Unterverzeichnis *TEMP*. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Entfernen der Beispielanwendung aus dem Cluster

Entfernen Sie die Beispielanwendung mithilfe des bereitgestellten Skripts von Ihrem Cluster.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Nächste Schritte

Im folgenden Artikel erhalten Sie weitere Informationen zur Funktionsweise des lokalen Prozesses mit Kubernetes:

> [!div class="nextstepaction"]
> [Funktionsweise des lokalen Prozesses mit Kubernetes](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-local-process-with-kubernetes.md