---
title: Erstellen und Bearbeiten von Buildkonfigurationen
description: In diesem Artikel wird beschrieben, wie Sie Buildkonfigurationen in Visual Studio für Mac erstellen.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: eb3ceed624e3bbba67564bb8f7c359841c0e496d
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939183"
---
# <a name="creating-and-editing-build-configurations"></a>Erstellen und Bearbeiten von Buildkonfigurationen

Buildkonfigurationen ermöglichen Ihnen die präzise Steuerung eines Builds, sodass Sie Konfigurationen erstellen können, die verschiedenen Test- und Verteilungssituationen gerecht werden. Sie können Buildkonfigurationen für einzelne Projekte oder für gesamte Projektmappen erstellen.

Sie können sowohl für Projekt als auch für Projektmappen mithilfe des Dialogfelds „Projektoptionen“ neue Konfigurationen erstellen und vorhandene bearbeiten.

>[!NOTE]
>Dieses Thema gilt für Visual Studio für Mac. Informationen für Visual Studio unter Windows finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Erstellen von Projektbuildkonfigurationen

Führen Sie die folgenden Schritte aus, um eine Projektbuildkonfiguration zu erstellen:

1. Klicken Sie mit der rechten Maustaste auf den Knoten „Projekte“, und klicken Sie dann auf **Options** (Optionen). Sie können auch auf den Projektknoten doppelklicken, um das Dialogfeld „Projektoptionen“ zu öffnen.

2. Klicken Sie im Dialogfeld „Projektoptionen“ auf **Build > Configurations** (Erstellen > Konfigurationen):

    ![Konfigurations-Manager in Projektoptionen](media/create-and-edit-configurations-image2.png)

3. Klicken Sie auf **Hinzufügen**, um eine neue Konfiguration zu erstellen. Sie können auch vorhandene Konfigurationen kopieren.

Sobald Sie die Konfiguration erstellt haben, können Sie den Abschnitt **Build** in den Projektoptionen verwenden, um die Eigenschaften gemäß Ihrer Konfigurationen anzupassen:

![Konfigurieren von Buildoptionen](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Erstellen einer Projektmappen-Buildkonfiguration

Führen Sie die folgenden Schritte aus, um eine Buildkonfiguration für eine Projektmappe zu erstellen:

1. Klicken Sie mit der rechten Maustaste auf den Projektmappenknoten, und wählen Sie **Optionen** aus. Sie können auf den Projektmappenknoten doppelklicken, um das Dialogfeld „Projektmappenoptionen“ zu öffnen.

2. Klicken Sie im Dialogfeld „Projektmappenoptionen“ auf **Build > Konfigurationen**:

    ![Konfigurations-Manager in Projektmappenoptionen](media/create-and-edit-configurations-image1.png)

3. Klicken Sie auf **Hinzufügen**, um eine neue Konfiguration zu erstellen. Sie können auch vorhandene Konfigurationen kopieren.

Sobald Sie die Konfiguration erstellt haben, können Sie den Abschnitt **Build** des Dialogfelds „Projektoptionen“ für alle Ihre Projekte verwenden, um die Eigenschaften gemäß Ihrer Konfigurationen anzupassen:

![Konfigurieren von Buildoptionen](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Umbenennen einer Buildkonfiguration

Wenn Sie eine Konfiguration umbenennen möchten, wählen Sie diese aus der Konfigurationsliste aus, indem Sie in den Projekt- oder Projektmappenoptionen zu **Build > Konfigurationen** navigieren:

![Konfigurationsliste](media/create-and-edit-configurations-image4.png)

Klicken Sie auf die Schaltfläche **Umbenennen**.

![Dialogfeld „Umbenennen“](media/create-and-edit-configurations-image5.png)

Klicken Sie dann zur Bestätigung auf **OK**.

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Siehe auch

- [Erstellen und Bearbeiten der Buildkonfiguration (Visual Studio unter Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)