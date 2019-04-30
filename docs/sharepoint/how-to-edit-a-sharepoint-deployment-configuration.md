---
title: 'Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffa7923bbe7e8a7b44fec280a5528ab023feed37
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444702"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration
  Sie können eine Bereitstellungskonfiguration erstellen oder eine vorhandene Bereitstellungskonfiguration zu ändern. Sie können z. B. einen einzigen Schritt ausführen oder Ändern der Reihenfolge der Schritte im Bereitstellungsprozess. Möglicherweise möchten erstellen oder Ändern von Bereitstellungskonfigurationen, da die integrierte und die programmgesteuert hinzugefügten Konfiguration nicht geändert werden können.

## <a name="create-a-sharepoint-deployment-configuration"></a>Erstellen Sie eine SharePoint-Bereitstellungskonfiguration

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Zum Erstellen einer SharePoint-Bereitstellungskonfiguration

1. In **Projektmappen-Explorer**, wählen Sie ein SharePoint-Projekt und dann auf der Menüleiste die Option **Projekt**, _ProjectName_**Eigenschaften**.

2. Auf der **SharePoint** Registerkarte die **neu** Schaltfläche.

     Die **neue Bereitstellungskonfiguration hinzufügen** Dialogfeld wird angezeigt.

3. In der **Namen** Text Geben Sie einen Namen für die Bereitstellungskonfiguration.

4. In der **Verfügbare Bereitstellungsschritte** Bereich, wählen Sie die Schritte aus, die Sie verwenden möchten, an der Bereitstellungskonfiguration hinzuzufügen, wählen Sie die (**>**) Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.

    > [!NOTE]
    > Wenn Sie einen Befehl vor der Bereitstellung oder ein Befehl nach der Bereitstellung konfiguriert haben, führen Sie diese Schritte nur, wenn Sie eine angepasste Bereitstellungskonfiguration hinzugefügt.

## <a name="change-the-active-deployment-configuration"></a>Ändern der aktiven Bereitstellungskonfiguration

#### <a name="to-change-the-active-deployment-configuration"></a>Die aktiven Bereitstellungskonfiguration ändern

1. In **Projektmappen-Explorer**, wählen Sie ein SharePoint-Projekt und dann auf der Menüleiste die Option **Projekt** > **\<*ProjectName*> Eigenschaften**.

2. Wählen Sie die **SharePoint** Registerkarte.

3. In der **aktive Bereitstellungskonfiguration** Listenfeld, wählen Sie den Namen der Bereitstellungskonfiguration, die Sie verwenden möchten.

## <a name="see-also"></a>Siehe auch
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
