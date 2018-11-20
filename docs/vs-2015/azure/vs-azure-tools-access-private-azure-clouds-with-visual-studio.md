---
title: Zugreifen auf private Azure-Clouds mit Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie private Cloudressourcen zugreifen, mithilfe von Visual Studio.
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002020"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Zugreifen auf private Azure-Clouds mit Visual Studio

Visual Studio unterstützt standardmäßig REST-Endpunkte für Azure-Cloud. In diesem Artikel erfahren Sie, wie Sie mit der privaten Cloud-Zertifikat zugreifen und interagieren mit der privaten Cloud in Visual Studio.

1. Klicken Sie im Azure-Portal für die private Cloud Datei mit den veröffentlichungseinstellungen herunter, oder wenden Sie sich an Ihren Administrator für eine Datei mit veröffentlichungseinstellungen. (Die Datei hat die Erweiterung `.publishsettings`.)

1. In Visual Studio **Server-Explorer**, mit der rechten Maustaste die **Azure** Knoten, und wählen **Abonnements verwalten und Filtern**.

    ![Verwalten von Abonnements-Befehl](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. In der **Microsoft Azure-Abonnements verwalten** wählen Sie im Dialogfeld die **Zertifikate** Registerkarte aus, und wählen Sie dann **Import**.

    ![Importieren von Azure-Zertifikaten](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. In der **Microsoft Azure-Abonnements importieren** wählen Sie im Dialogfeld **Durchsuchen**.

    ![Navigieren Sie auf das Dialogfeld "Microsoft Azure-Abonnements importieren" auf die Schaltfläche](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. In der **öffnen** Dialogfeld, navigieren Sie zu dem Verzeichnis, in dem Sie die Datei mit veröffentlichungseinstellungen gespeichert, wählen Sie die Datei, und wählen Sie dann **öffnen**.

    ![Wählen Sie die Datei mit veröffentlichungseinstellungen](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Rückkehr zum die **Microsoft Azure-Abonnements importieren** wählen Sie im Dialogfeld **Import**.

    ![Die Datei mit veröffentlichungseinstellungen importieren](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Die Zertifikate werden in Visual Studio aus der Datei mit veröffentlichungseinstellungen importiert, und Sie können jetzt mit Ihrer privaten Cloudressourcen interagieren.

