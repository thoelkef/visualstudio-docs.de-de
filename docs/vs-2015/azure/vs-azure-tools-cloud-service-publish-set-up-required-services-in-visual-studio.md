---
title: Veröffentlichen und Bereitstellen eines Clouddiensts in Visual Studio | Microsoft-Dokumentation
description: Informationen Sie zu den Vorgehensweisen zum Einrichten von Cloud und speicherkontodiensten und konfigurieren die Azure-Anwendung.
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d7643d87f60b953b9c0928571036c7890e4d11f0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002029"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Vorbereiten der Veröffentlichung und Bereitstellung eines Clouddiensts über Visual Studio

Um ein clouddienstprojekt veröffentlichen zu können, müssen Sie die folgenden Dienste einrichten, wie in diesem Artikel beschrieben:

* Ein **cloud-Dienst** zum Ausführen Ihrer Rollen in Azure-Umgebung, und 
* Ein **Speicherkonto** , Zugriff auf die BLOB-, Warteschlangen- und Tabelle Dienste bereitstellt.

## <a name="create-a-cloud-service"></a>Erstellen Sie einen Clouddienst

Ein Clouddienst führt Ihre Rollen in Azure-Umgebung. Sie können einen Cloud-Dienst in Visual Studio oder durch Erstellen der [Azure-Portal](https://portal.azure.com/) wie in den Abschnitten beschrieben.

### <a name="create-a-cloud-service-from-visual-studio"></a>Erstellen Sie einen Clouddienst über Visual Studio

1. Ein zuvor erstelltes clouddienstprojekt mit der rechten Maustaste der Projekt, und wählen **veröffentlichen**.
1. Falls erforderlich, melden Sie sich mit dem Microsoft- oder organisationskonto an, die mit Ihrem Azure-Abonnement verknüpft ist, und wählen Sie dann **Weiter** , fahren Sie fort, um die **Einstellungen** Seite.
1. Ein **Cloud-Dienst erstellen und Storage-Konto** Dialogfeld wird angezeigt (wenn nicht der Fall, wählen Sie **neu erstellen** aus der **Cloud-Dienst** Liste).
1. Geben Sie einen Groß-/Kleinschreibung Namen für Ihren Clouddienst, der Teil Ihrer URL und muss eindeutig sein. Außerdem wählen Sie eine Region oder Affinitätsgruppe aus, und wählen Sie eine Replikation aus.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Erstellen Sie einen Clouddienst über das Azure-portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.
1. Wählen Sie **Clouddienste (klassisch)** auf der linken Seite der Seite.
1. Wählen Sie **+ Add**, geben Sie dann die erforderliche Informationen (DNS-Name, Abonnement, Ressourcengruppe und Standort). Es ist nicht erforderlich, ein Paket an diesem Punkt hochgeladen werden, da Sie dies später in Visual Studio tun.
1. Wählen Sie **erstellen** um den Vorgang abzuschließen.

## <a name="create-a-storage-account"></a>Erstellen eines Speicherkontos

Ein Speicherkonto bietet Zugriff auf die BLOB-, Warteschlangen- und Tabelle. Sie können ein Speicherkonto mithilfe von Visual Studio erstellen oder die [Azure-Portal](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Erstellen eines Speicherkontos in Visual Studio

1. In **Projektmappen-Explorer** mit einem zuvor erstellten-Dienst-clouddienstprojekt, suchen Sie die **verbundene Dienste** Knoten innerhalb einer rollenprojekt, mit der rechten Maustaste, und wählen **verbundenen Dienst hinzufügen**. (In Visual Studio 2015, mit der Maustaste der **Storage** Knoten, und wählen **Create Storage Account**.)
1. In der **verbundene Dienste** Liste, die angezeigt wird, wählen Sie **Cloudspeicher mit Azure Storage**.
1. Azure-Speicher, der angezeigt wird, wählen Sie im Dialogfeld **+ neues Speicherkonto erstellen**, worauf ein Dialogfeld, in dem Sie Ihr Abonnement, einen Namen angeben, für das Konto, ein Tarif Tarif, Ressourcengruppe und Standort.
1. Wählen Sie **erstellen** Wenn Sie fertig sind. Das neue Speicherkonto wird in der Liste der verfügbaren Speicherkonten in Ihrem Abonnement angezeigt.
1. Wählen Sie die Konto, und wählen Sie **hinzufügen**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Erstellen eines Speicherkontos über das Azure-portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.
1. Wählen Sie **+ neu** auf der oberen linken Ecke.
1. Wählen Sie **Storage** unter "Azure Marketplace" dann **Speicherkonto – Blob, Datei, Tabelle, Warteschlange** auf der rechten Seite.
1. Geben Sie die erforderlichen Informationen (Name, Bereitstellungsmodell und So weiter.
1. Wählen Sie **erstellen** um den Vorgang abzuschließen.

## <a name="configure-your-app-to-use-the-storage-account"></a>Konfigurieren Sie Ihrer app für das Speicherkonto verwenden

Nachdem Sie ein Speicherkonto erstellt, aktualisiert die Verbindung mit der sie aus Visual Studio automatisch die Dienstkonfigurationen für das Projekt, einschließlich URLs und Zugriffsschlüssel.

Wenn Sie einen Cloud-Dienst von der Verwendung von Visual Studio erstellt die **verbundenen Dienst hinzufügen**, können Sie die Verbindungen überprüfen, indem Sie Sie öffnen `ServiceConfiguration.Cloud.cscfg` und `ServiceConfiguration.Local.cscfg`.

Wenn Sie einen Cloud-Dienst über das Azure-Portal erstellt haben, führen Sie die gleichen Schritte in [erstellen Sie ein Speicherkonto in Visual Studio](#create-a-storage-account-from-visual-studio) aber wählen Sie das vorhandene Konto, anstatt einen neuen zu erstellen. Visual Studio aktualisiert dann die Konfiguration für Sie.

So konfigurieren Sie Einstellungen manuell, verwenden Sie die Eigenschaftenseiten in Visual Studio für die jeweilige Rolle in Ihrem Cloud-Dienstprojekt (mit der rechten Maustaste in der Rolle, und wählen Sie **Eigenschaften**). Weitere Informationen finden Sie unter [Konfigurieren einer Verbindungszeichenfolge mit einem Speicherkonto](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Informationen zu Zugriffsschlüsseln

Das Azure-Portal zeigt die URLs, die Sie verwenden können, um den Zugriff auf Ressourcen in jeder Azure-Speicherdienste sowie die primären und sekundären Zugriffsschlüssel für Ihr Konto. Sie verwenden diesen Schlüssel zum Authentifizieren von Anforderungen für die Storage-Dienste.

Der sekundäre Zugriffsschlüssel bietet denselben Zugriff auf Ihr Speicherkonto wie der primäre Zugriffsschlüssel und wird als Reserveschlüssel generiert Ihre primären Zugriffsschlüssels gefährdet sein sollte. Darüber hinaus empfiehlt es sich, dass Sie Ihre Zugriffsschlüssel regelmäßig neu generieren. Sie können ändern, dass eine Verbindungszeichenfolge zu den sekundären Schlüssel verwenden, während Sie den primären Schlüssel neu generieren, Sie ändern können, um den neu generierten primären Schlüssel zu verwenden, während Sie den sekundären Schlüssel neu generieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Veröffentlichen von apps in Azure aus Visual Studio finden Sie unter [Veröffentlichen eines Clouddiensts mit den Azure Tools](vs-azure-tools-publishing-a-cloud-service.md).
