---
title: Erstellen eines Azure-clouddienstprojekts mit Visual Studio | Microsoft-Dokumentation
description: Beschrieben, wie Sie ein Azure-Cloud-Service-Projekt mit Visual Studio erstellen
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002059"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Erstellen eines Azure-clouddienstprojekts mit Visual Studio
Die Azure Tools für Visual Studio enthält eine Projektvorlage, die Sie erstellen kann eine [Azure-Clouddienst](/azure/cloud-services/cloud-services-choose-me), einen einfachen allgemeinen Azure-Dienst. Nachdem das Projekt erstellt wurde, können in Visual Studio Sie konfigurieren, Debuggen und Bereitstellen von Cloud-Dienst in Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Schritte zum Erstellen einer Azure-Cloud-Dienstprojekt in Visual Studio
Dieser Abschnitt führt Sie durch Erstellen einer Azure-Cloud-Dienstprojekt in Visual Studio mit einer oder mehreren Webrollen.  

1. Starten Sie Visual Studio als Administrator an.

1. Wählen Sie im Hauptmenü **Datei** > **neu** > **Projekt**.

1. Wählen Sie **Cloud** aus der Visualisierung C# oder Visual Basic projektvorlagenknoten, und wählen **Azure-Clouddienst** aus der Liste der Vorlagen.

    ![Neuen Azure-Cloud-Dienst](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Geben Sie die Version von .NET Framework zur Entwicklung Ihres Projekts verwenden möchten.

1. Geben Sie einen Namen und Speicherort für das Projekt und einen Namen für die Lösung. 

1. Klicken Sie auf **OK**.

1. In der **neuen Microsoft Azure-Cloud-Dienst** Dialogfeld Wählen Sie die Rollen, die Sie hinzufügen möchten, und wählen Sie den Pfeil nach rechts-Schaltfläche, um sie der Projektmappe hinzuzufügen.

    ![Wählen Sie die neue Azure-Cloud-Service-Rollen](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Um eine Rolle umzubenennen, die Sie hinzugefügt haben, zeigen Sie auf die Rolle in der **neuen Microsoft Azure-Cloud-Dienst** Dialogfeld, und wählen Sie im Kontextmenü der **umbenennen**. Sie können auch eine Rolle in der Projektmappe umbenennen (in der **Projektmappen-Explorer**), nachdem er hinzugefügt wurde.

    ![Benennen Sie die Azure-Cloud-Dienstrolle](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Das Visual Studio-Azure-Projekt weist Zuordnungen zu den rollenprojekten in der Projektmappe. Das Projekt enthält zudem die *dienstdefinitionsdatei* und *Dienstkonfigurationsdatei*:

- **Dienstdefinitionsdatei** -definiert die Laufzeiteinstellungen für Ihre Anwendung, u. a. welche Rollen erforderlich sind, Endpunkte und Größe des virtuellen Computers. 
- **Dienstkonfigurationsdatei** -konfiguriert, wie viele Instanzen einer Rolle ausgeführt und die Werte der Einstellungen für eine Rolle definiert sind. 

Weitere Informationen zu diesen Dateien finden Sie unter [Konfigurieren der Rollen für Azure-Clouddienst mit Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Nächste Schritte
- [Verwalten von Rollen in Azure-clouddienstprojekten mit Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
