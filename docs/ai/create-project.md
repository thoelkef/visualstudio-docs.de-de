---
title: "Erstellen eines Projekts mit KI-Tools für Visual Studio"
description: Erstellen eines Projekts mithilfe des Beispiels aus dem Azure Machine Learning-Katalog
keywords: KI, Visual Studio, Azure Machine Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.technology: visual studio
ms.devlang: multiple
ms.service: multiple
ms.openlocfilehash: 2d8b5f1d06d31eaba9c75e0f0515b2526fc7efdf
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Erstellen eines KI-Projekts aus dem Azure Machine Learning-Katalog in Visual Studio

Azure Machine Learning ist in Visual Studio-Tools für KI enthalten. Sie können diesen Dienst verwenden, um Machine Learning-Aufträge an Remotecomputeziele wie virtuelle Azure-Computer, Spark-Cluster usw. zu übermitteln. Weitere Informationen zu [Azure Machine Learning-Experimentieren](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration) 

Wenn Sie die [Visual Studio-Tools für KI](installation.md) installiert haben, lässt sich anhand der Anleitungen im Azure Machine Learning-Beispielkatalog ganz einfach ein neues Python-Projekt erstellen.

> ! Azure Machine Learning Workbench muss installiert sein. Weitere Informationen zur Installation finden Sie unter [Schnellstart für die Azure Machine Learning-Installation](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation). 

1. Starten Sie Visual Studio. Öffnen Sie den **Server-Explorer**, indem Sie das Menü **AI Tools** (KI-Tools) öffnen und auf **Cluster auswählen** klicken.  

    ![Clusterauswahl](media\create-project\select-cluster.png)

1. Melden Sie sich bei Ihrem Azure Machine Learning-Abonnement an, indem Sie mit der rechten Maustaste auf den Knoten **Azure Machine Learning** im Server-Explorer und dann auf **Anmeldung** klicken und die Anweisungen befolgen.

    ![Anmeldung](media\create-project\azureml-login.png)
 
2. Klicken Sie auf **AI Tools > Azure Machine Learning Sample Gallery** (KI-Tools > Azure Machine Learning-Beispielkatalog). 
    
    ![Beispielkatalog](media\create-project\gallery.png)

1. Wählen Sie für diesen Schnellstart das Beispiel „**MNIST mit TensorFlow**“ aus, und klicken Sie auf **Installieren**. Stellen Sie Folgendes bereit: 
2.
 - **Ressourcengruppe:** die Azure-Ressourcengruppe, in der Ihre Metadaten gespeichert werden
 - **Konto:** das Konto für Azure Machine Learning-Experimentieren
 - **Arbeitsbereich:** der Azure Machine Learning-Arbeitsbereich
 - **Projekttyp:** das Machine Learning-Framework Wählen Sie in diesem Fall **TensorFlow** aus.
 - **Zur Projektmappe hinzufügen:** bestimmt, ob Ihre aktuelle Visual Studio-Projektmappe hinzugefügt oder eine neue Projektmappe erstellt und geöffnet werden soll
 - **Projektpfad:** Speicherort des Codes
 - **Projektname:** Geben Sie **TensorFlowMNIST** ein.
   

    ![Das resultierende Projekt, wenn die Python-Anwendungsvorlage verwendet wird.](media\create-project\new-AzureSampleProject.png)

1. Visual Studio erstellt die Projektdatei (eine `.pyproj`-Datei auf dem Datenträger) zusammen mit anderen Dateien, die im Beispiel definiert sind. Mit der MNIST-Vorlage enthält das Projekt mehrere Dateien.

    ![MNIST](media\create-project\azml-mnist.png)

1. Übermitteln Sie den Auftrag an Azure Machine Learning. 

    ![MNIST](media\create-project\submit-azml.png)

1. Führen Sie diesen in einem Docker-Container oder auf Ihrem lokalen virtuellen Computer aus.

    ![MNIST](media\create-project\azml-local.png)