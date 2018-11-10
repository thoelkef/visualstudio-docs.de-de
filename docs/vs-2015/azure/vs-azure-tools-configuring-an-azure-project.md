---
title: Konfigurieren ein Azure-clouddienstprojekts mit Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Azure-Cloud-Service-Projekt in Visual Studio, je nach Ihren Anforderungen für dieses Projekt zu konfigurieren.
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 7417bc117de7dc472f413dd9145944cad2d48bb4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002014"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Konfigurieren von Azure-Clouddienstprojekten mit Visual Studio
Sie können eine Azure-clouddienstprojekt abhängig von den Anforderungen für dieses Projekt konfigurieren. Sie können Eigenschaften für das Projekt für die folgenden Kategorien festlegen:

- **Veröffentlichen eines Clouddiensts in Azure** – Sie können festlegen, eine Eigenschaft, um sicherzustellen, dass es sich bei ein vorhandenen Clouddienst in Azure bereitgestellten nicht versehentlich gelöscht wird.
- **Ausführen oder Debuggen ein Clouddiensts auf dem lokalen Computer** – Sie können eine Dienstkonfiguration auswählen und angeben, ob den Azure-Speicheremulator gestartet werden soll.
- **Überprüfen ein clouddienstpakets, bei der Erstellung wird** -können Sie entscheiden, alle Warnungen als Fehler behandelt werden, damit können Sie sicherstellen, dass das clouddienstpaket ohne Probleme bereitgestellt. 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Schritte zum Konfigurieren einer Azure-Cloud-Dienstprojekt
1. Öffnen Sie oder erstellen Sie ein clouddienstprojekt in Visual Studio

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Projekts und wählen Sie im Kontextmenü des **Eigenschaften**.
   
1. Wählen Sie in der Eigenschaftenseite des Projekts die **Entwicklung** Registerkarte.

    ![Menü "Projekt-Eigenschaften"](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Legen Sie **vor dem Löschen einer vorhandenen Bereitstellung Fragen** zu **"true"**. Mit dieser Einstellung können, um sicherzustellen, dass Sie nicht versehentlich eine vorhandene Bereitstellung in Azure löschen

1. Wählen Sie den gewünschten **Dienstkonfiguration** an der Dienstkonfiguration beim Ausführen oder Debuggen Ihren Clouddienst lokal verwendet werden sollen. Weitere Informationen zum Ändern einer Dienstkonfiguration für eine Rolle finden Sie unter [so konfigurieren Sie die Rollen für Azure-Clouddienst mit Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Legen Sie **Azure-Speicheremulator starten** zu **"true"** des Azure-Speicheremulators beim Ausführen oder des Clouddiensts lokal Debuggen zu starten.

1. Legen Sie **Warnungen als Fehler behandeln** zu **"true"** um sicherzustellen, dass kann nicht veröffentlicht werden, wenn das paketvalidierungsfehler vorhanden sind.

1. Legen Sie **Webprojektports** zu **"true"** , stellen Sie sicher, dass die Web-Rolle den gleichen Port verwendet, bei jeder Ausführung lokalen Start in IIS Express.

1. Wählen Sie in der Symbolleiste von Visual Studio **speichern**.

## <a name="next-steps"></a>Nächste Schritte
- [Konfigurieren eines Azure-Projekts mit mehreren Dienstkonfigurationen](vs-azure-tools-multiple-services-project-configurations.md)

