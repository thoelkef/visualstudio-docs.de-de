---
title: Erstellen eines Projekts mit KI-Tools für Visual Studio
description: Erstellen eines Projekts mithilfe des Beispiels aus dem Azure Machine Learning-Katalog
keywords: KI, Visual Studio, Azure Machine Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 495c0d256fc6c8f36ded67166f7d12aace7a9202
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Erstellen eines KI-Projekts aus dem Azure Machine Learning-Katalog in Visual Studio

Azure Machine Learning ist in Visual Studio-Tools für KI enthalten. Sie können diesen Dienst verwenden, um Machine Learning-Aufträge an Remotecomputeziele wie virtuelle Azure-Computer, Spark-Cluster usw. zu übermitteln. Weitere Informationen zu [Azure Machine Learning-Experimentieren](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration)

Wenn Sie die [Visual Studio-Tools für KI](installation.md) installiert haben, lässt sich anhand der Anleitungen im Azure Machine Learning-Beispielkatalog ganz einfach ein neues Python-Projekt erstellen.

> [!NOTE]
> Azure Machine Learning Workbench muss installiert sein. Weitere Informationen zur Installation finden Sie unter [Schnellstart für die Azure Machine Learning-Installation](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation).

1. Starten Sie Visual Studio. Öffnen Sie den **Server-Explorer**, indem Sie das Menü **AI Tools** (KI-Tools) öffnen und auf **Cluster auswählen** klicken.

    ![Clusterauswahl](media\create-project-gallery\select-cluster.png)

1. Melden Sie sich bei Ihrem Azure Machine Learning-Abonnement an, indem Sie mit der rechten Maustaste auf den Knoten **Azure Machine Learning** im Server-Explorer und dann auf **Anmeldung** klicken und die Anweisungen befolgen.

    ![Anmeldung](media\create-project-gallery\azureml-login.png)

2. Klicken Sie auf **AI Tools > Azure Machine Learning Sample Gallery** (KI-Tools > Azure Machine Learning-Beispielkatalog).

    ![Beispielkatalog](media\create-project-gallery\gallery.png)

1. Wählen Sie für diesen Schnellstart das Beispiel „**MNIST mit TensorFlow**“ aus, und klicken Sie auf **Installieren**. Geben Sie hierzu folgende Informationen an:

 - **Ressourcengruppe**: Die Azure-Ressourcengruppe, in der Ihre Metadaten gespeichert werden
 - **Konto**: Das Konto für Azure Machine Learning-Experimentieren
 - **Arbeitsbereich**: Der Azure Machine Learning-Arbeitsbereich
 - **Projekttyp**: Das Machine Learning-Framework Wählen Sie in diesem Fall **TensorFlow** aus.
 - **Zur Projektmappe hinzufügen**: Bestimmt, ob Ihre aktuelle Visual Studio-Projektmappe hinzugefügt oder eine neue Projektmappe erstellt und geöffnet werden soll
 - **Projektpfad**: Speicherort des Codes
 - **Projektname**: Geben Sie **TensorFlowMNIST** ein.

![Das resultierende Projekt, wenn die Python-Anwendungsvorlage verwendet wird](media/create-project-gallery/new-AzureSampleProject.png)

1. Visual Studio erstellt die Projektdatei (eine `.pyproj`-Datei auf dem Datenträger) zusammen mit anderen Dateien, die im Beispiel definiert sind. Mit der MNIST-Vorlage enthält das Projekt mehrere Dateien.

    ![MNIST](media\create-project-gallery\azml-mnist.png)

1. Übermitteln Sie den Auftrag an Azure Machine Learning.

    ![MNIST](media\create-project-gallery\submit-azml.png)

1. Führen Sie diesen in einem Docker-Container oder auf Ihrem lokalen virtuellen Computer aus.

    ![MNIST](media\create-project-gallery\azml-local.png)