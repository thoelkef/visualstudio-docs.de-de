---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud mit Visual Studio, Schritt 3: Erstellen einer Kubernetes-Entwicklungsumgebung | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 6226340b1744e95bbb375d47213ae00bb9e76565
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884384"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Erste Schritte in Connected Environment mit .NET Core und Visual Studio

Vorheriger Schritt: [Erstellen von ASP.NET-Web-Apps](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Erstellen einer Entwicklungsumgebung in Azure
Mit Connected Environment können Sie auf Kubernetes basierende Umgebungen erstellen, die vollständig von Azure verwaltet werden und für die Entwicklung optimiert sind. Öffnen Sie das zuvor erstellte Projekt, und klicken Sie wie unten dargestellt in der Dropdownliste „Starteinstellungen“ auf **Connected Environment for AKS** (Connected Environment für AKS).

![](images/LaunchSettings.png)

Überprüfen Sie in dem daraufhin angezeigten Dialogfeld, ob Sie mit dem richtigen Konto angemeldet sind, und wählen Sie anschließend entweder eine bereits vorhandene Entwicklungsumgebung oder **<Create New Connected Environment for AKS…>** (Neue Connected Environment für AKS erstellen) aus, um eine neue Entwicklungsumgebung zu erstellen.

![](images/ConnectedEnvDialog.png)

Sie können die bereitgestellten Standardwerte verwenden bzw. diese nach Belieben anpassen. Klicken Sie auf **OK**, wenn die Werte richtig festgelegt sind.

![](images/NewEnvDialog.png)

Verändern Sie die Standardeinstellung (`mainline`) für die Dropdownliste unter **Bereich** noch nicht. Diese Einstellung wird später noch ausführlicher erläutert. Aktivieren Sie das Feld **Publicly Accessible** (Öffentlich zugänglich), damit über einen öffentlichen Endpunkt auf die Web-App zugegriffen werden kann. Dieser Schritt ist zwar nicht erforderlich, aber er vereinfacht die Darstellung einiger weiterer Konzepte, die Teil dieser exemplarischen Vorgehensweise sind. Sie können aber Ihre Website auch mithilfe von Visual Studio debuggen, wenn Sie dieses Feld nicht aktivieren.

![](images/ConnectedEnvDialog2.png)

Klicken Sie auf **OK**, um die Entwicklungsumgebung auszuwählen oder zu erstellen. Dann wird eine Hintergrundaufgabe gestartet, die innerhalb weniger Minuten den Erstellvorgang abschließt. Sie können überprüfen, ob der Vorgang bereits abgeschlossen wurde, indem Sie mit Ihrem Cursor auf das Symbol **Hintergrundaufgaben** im unteren Bereich auf der linken Seite der Statusleiste (im Folgenden abgebildet) zeigen.

![](images/BackgroundTasks.png)

> [!Note]
Sie können Ihre Anwendung erst debuggen, wenn die Entwicklungsumgebung erfolgreich erstellt wurde.

## <a name="look-at-the-files-added-to-project"></a>Die dem Projekt hinzugefügten Dateien
Während Sie darauf warten, dass die Entwicklungsumgebung erstellt wird, können Sie sich die Dateien ansehen, die zu Ihrem Projekt hinzugefügt wurden, als Sie sich dafür entschieden haben, eine Entwicklungsumgebung zu verwenden.

Als Erstes sehen Sie einen Ordner mit dem Namen `charts` und darin ein [Helm-Diagramm](https://docs.helm.sh), da Ihrer Anwendung ein Gerüst hinzugefügt wurde. Diese Dateien werden verwendet, um Ihre Anwendung in der Entwicklungsumgebung bereitzustellen.

Außerdem sollten Sie feststellen, dass eine Datei mit dem Namen `Dockerfile` hinzugefügt wurde. Diese Datei enthält Informationen, die zum Packen Ihrer Anwendung in das Standardformat für Docker benötigt werden. Zudem wird eine `HeaderPropagation.cs`-Datei erstellt, die nachfolgend in dieser exemplarischen Vorgehensweise erläutert wird. 

Zuletzt sollte die Datei mit dem Namen `vsce.yaml` angezeigt werden. Diese Datei enthält Informationen, die von der Entwicklungsumgebung für die Konfiguration benötigt werden. Beispielsweise ist darin festgelegt, ob die Anwendung über einen öffentlichen Endpunkt zugänglich sein soll.

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Debuggen eines Containers in Kubernetes](get-started-netcore-visualstudio-04.md)