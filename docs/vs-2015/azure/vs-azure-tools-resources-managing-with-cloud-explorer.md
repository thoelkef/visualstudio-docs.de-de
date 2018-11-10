---
title: Verwalten von Azure-Ressourcen mit Cloud-Explorer | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit der Cloud-Explorer zum Durchsuchen und Verwalten von Azure-Ressourcen in Visual Studio.
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001714"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Verwalten der Ihren Azure-Konten im Visual Studio Cloud-Explorer zugeordneten Ressourcen

Cloud-Explorer können Sie Ihre Azure-Ressourcen und Ressourcengruppen anzeigen, deren Eigenschaften überprüfen und wichtige Diagnosen entwickleraktionen in Visual Studio ausführen. 

Wie die [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud-Explorer auf dem Azure Resource Manager-Stapel erstellt wird. Aus diesem Grund erkennt Cloud-Explorer, Ressourcen wie Azure-Ressourcengruppen und Azure-Diensten wie Logic apps und API-apps und unterstützt [Role-based Access Control,](/azure/role-based-access-control/role-assignments-portal.md) (RBAC). 

## <a name="prerequisites"></a>Vorraussetzungen

* Visual Studio 2015 mit dem [Microsoft Azure SDK für .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Microsoft Azure-Konto – Wenn Sie kein Konto besitzen, können Sie [registrieren Sie sich für eine kostenlose Testversion](http://go.microsoft.com/fwlink/?LinkId=623901) oder [Ihre Visual Studio-abonnentenvorteile aktivieren](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Wählen Sie zum Anzeigen von Cloud-Explorer **Ansicht** > **Cloud-Explorer** in der Menüleiste.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Hinzufügen eines Azure-Konto zum Cloud-Explorer

Um die Azure-Konto zugeordneten Ressourcen anzuzeigen, müssen Sie das Konto zuerst zum Cloud-Explorer hinzufügen. 

1. In **Cloud-Explorer**Option **Azure-kontoeinstellungen**.

   ![Symbol "Einstellungen" Cloud-Explorer-Azure-Konto](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Wählen Sie **Verwalten von Konten**. 

   ![Link für Cloud-Explorer-Konto hinzufügen](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Melden Sie sich an den Azure-Konto, dessen Ressourcen Sie durchsuchen möchten. 

1. Sobald Sie angemeldet sind, um ein Azure-Konto, zeigen die mit diesem Konto verknüpften Abonnements. Wählen Sie die Kontrollkästchen für die Kontoabonnements, die Sie verwenden möchten, suchen und wählen Sie dann **übernehmen**. 

   ![Cloud-Explorer: Wählen Sie anzuzeigende Azure-Abonnements](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Nach der Auswahl der Abonnements, deren Ressourcen Sie durchsuchen möchten, zeigen diese Abonnements und Ressourcen im Cloud-Explorer aus.

   ![Cloud-Explorer-Ressourcenliste für ein Azure-Konto](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Entfernen Sie ein Azure-Konto im Cloud-Explorer 

1. In **Cloud-Explorer**Option **Kontoverwaltung**.

   ![Symbol "Einstellungen" Cloud-Explorer-Azure-Konto](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Wählen Sie neben dem Konto, das Sie entfernen möchten, **Verwalten von Konten**.

   ![Symbol "Einstellungen" Cloud-Explorer-Azure-Konto](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Wählen Sie **entfernen** um ein Konto zu entfernen.

    ![Cloud-Explorer Verwalten von Konten (Dialogfeld)](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Anzeigen von Ressourcentypen oder Ressourcengruppen

Um Ihre Azure-Ressourcen anzuzeigen, wählen Sie entweder **Ressourcentypen** oder **Ressourcengruppen** anzeigen.

1. In **Cloud-Explorer**, wählen Sie die Dropdownliste für die Ressourcenansicht.

   ![Cloud-Explorer-Dropdownliste zum Auswählen der gewünschten Ressourcenansicht](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Wählen Sie im Kontextmenü die gewünschte Ansicht aus: 

   * **Ressourcentypen** anzeigen – die übliche Ansicht der [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040), zeigt Ihre Azure-Ressourcen Typkategorien, z. B. Web-apps, Speicherkonten und virtuelle Computer. 
   * **Ressourcengruppen** anzeigen: Zeigt Azure-Ressourcen von Azure-Ressourcengruppe mit dem sie zugeordnet sind. Eine Ressourcengruppe ist ein Bündel von Azure-Ressourcen in der Regel eine bestimmte Anwendung verwendet. Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter [Übersicht über Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   Die folgende Abbildung zeigt einen Vergleich der beiden Ressourcenansichten:

   ![Cloud-Explorer-Ressourcenansichten](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Zeigen Sie an von und navigieren Sie Ressourcen im Cloud-Explorer

Klicken Sie zum Navigieren zu einer Azure-Ressource aus, und die Informationen im Cloud-Explorer anzuzeigen, erweitern Sie Typ oder die zugeordnete Ressourcengruppe des Elements, und wählen Sie dann auf die Ressource. Wenn Sie eine Ressource auswählen, Informationen angezeigt, auf den beiden Registerkarten - **Aktionen** und **Eigenschaften** : am unteren Rand der Cloud-Explorer.

* **Aktionen** Registerkarte: führt die Aktionen, die Sie im Cloud-Explorer für die ausgewählte Ressource ausführen können. Sie können diese Optionen auch anzeigen, durch Rechtsklick auf die Ressource, um das Kontextmenü anzuzeigen.

* **Eigenschaften** Registerkarte: Zeigt die Eigenschaften der Ressource, z.B. Typ, Gebietsschema und die Ressourcengruppe mit dem es verknüpft ist.

Die folgende Abbildung zeigt einen Beispiel-Vergleich von was Sie auf jeder Registerkarte für eine App Service finden Sie unter:

  ![Screenshot des Cloud-Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Jede Ressource verfügt über die Aktion **im Portal öffnen**. Wenn Sie diese Aktion auswählen, zeigt der Cloud-Explorer die ausgewählte Ressource im der [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). Die **im Portal öffnen** Funktion ist nützlich für die Navigation zu tief geschachtelten Ressourcen.

Zusätzliche Aktionen und Eigenschaftswerte können auch basierend auf der Azure-Ressource angezeigt. Angenommen, Web-apps und Logik-apps auch verfügen über die Aktionen **im Browser öffnen** und **Debugger Anfügen** zusätzlich zu **im Portal öffnen**. Aktionen zum Öffnen von Editoren werden angezeigt, wenn Sie ein Speicherkonto-Blob, Warteschlange oder Tabelle auswählen. Azure-apps stehen **URL** und **Status** Eigenschaften, während Speicherressourcen Schlüssel und Verbindungszeichenfolgen-Eigenschaften aufweisen.

## <a name="find-resources-in-cloud-explorer"></a>Suchen von Ressourcen im Cloud-Explorer

Um in Ihren Azure-Kontoabonnements Ressourcen mit einem bestimmten Namen suchen, geben Sie auf den Namen in der **Suche** Feld im Cloud-Explorer.

  ![Suchen von Ressourcen im Cloud-Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Eingabe von Zeichen in der **Suche** Feld nur Ressourcen, die diese Zeichen entsprechen, die in der Ressourcenstruktur angezeigt werden.
