---
title: Senden eines Auftrags zum Trainieren eines Modells in Azure Batch AI
description: Training Model Cloud
keywords: KI, Visual Studio, Modell trainieren, Cloud
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: dec70c9e9aeb9c916b511241a74b550354aff175
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915775"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Trainieren von KI-Modellen in Azure Batch AI

Azure Batch AI ist ein verwalteter Dienst, mit dem Datenanalysten und KI-Forscher KI und andere Machine Learning-Modelle in Clustern von virtuellen Azure-Computern trainieren können (inkl. VMs mit GPU-Unterstützung). Sie müssen nur beschreiben, welche Anforderungen für den Auftrag bestehen und wo die Eingaben zu finden sind sowie die Ausgaben speichern, und Batch AI übernimmt den Rest. [Weitere Informationen zu Azure Batch AI](/azure/batch-ai/overview)

Da Batch AI mit den Visual Studio-Tools für KI integriert wird, können Sie Trainingsmodelle in Azure dynamisch horizontal hochskalieren.  Wenn Sie die [Visual Studio-Tools für KI](installation.md) installiert haben, lässt sich anhand der Anleitungen im Azure Machine Learning-Beispielkatalog ganz einfach ein neues Python-Projekt erstellen.

1. Starten Sie Visual Studio. Öffnen Sie den **Server-Explorer**, indem Sie das Menü **AI Tools** (KI-Tools) öffnen und auf **Cluster auswählen** klicken.

    ![Clusterauswahl](media/train-model/select-cluster.png)

2. Erweitern Sie **AI Tools** (KI-Tools). Jede Ihrer Batch AI-Ressourcen wird automatisch erkannt und im Server-Explorer angezeigt.

    ![Beispielkatalog](media/train-model/batchai.png)

3. Klicken Sie auf **Ansicht > Team Explorer...** , um das Fenster **Team Explorer** zu öffnen. Dort können Sie eine Verbindung zu GitHub oder Azure DevOps herstellen oder ein Repository klonen.

    ![Das Team Explorer-Fenster zeigt Azure DevOps, GitHub und das Klonen eines Repositorys an.](media/train-model/team-explorer-devops.png)

4. Geben Sie `https://github.com/Microsoft/samples-for-ai` im Feld „URL“ unter **Lokale Git-Repositorys** ein. Geben Sie einen Ordner für die geklonten Dateien an, und klicken Sie auf **Klonen**.

    > [!Tip]
    > Der Ordner, den Sie in Team Explorer angeben, empfängt die geklonten Dateien. Im Gegensatz zum Befehl `git clone` wird beim Erstellen eines Klons in Team Explorer nicht automatisch ein Unterordner mit dem Namen des Repositorys erstellt.

5. Wenn das Klonen abgeschlossen ist, klicken Sie auf **Datei > Projektmappe öffnen > Projekt/Projektmappe**.

    ![Beispielkatalog](media/train-model/open-solution.png)

6. Öffnen Sie **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** im Verzeichnis, das Sie im Repository geklont haben.

    ![Beispielkatalog](media/train-model/tensorflowexamples.png)

7. Legen Sie das MNIST-Projekt als **Startprojekt** fest.

    ![Beispielkatalog](media/train-model/mnist-startup.png)

8. <strong>Klicken Sie mit der rechten Maustaste auf das **MNIST-Projekt** und dann auf **Auftrag übermitteln**</strong>.

    ![Beispielkatalog](media/train-model/submit-job.png)
9. Wählen Sie Ihr **Azure Batch AI**-Cluster aus, und klicken Sie auf **Importieren**. Wählen Sie die Datei `AzureBatchAI_TF_MNIST.json` aus, um schnell einige Standardwerte wie das zu verwendende Docker-Image aufzufüllen. Klicken Sie dann auf **Senden**.

    ![Beispielkatalog](media/train-model/submit-batch.png)
