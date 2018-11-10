---
title: Einrichten benannter Authentifizierungsanmeldeinformationen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Anmeldeinformationen angeben, die mithilfe von Visual Studio zum Authentifizieren von Anforderungen an Azure, damit Sie einer Anwendung in Azure aus Visual Studio veröffentlichen oder einen vorhandenen Clouddienst überwachen können.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001990"
---
# <a name="set-up-named-authentication-credentials"></a>Einrichten von benannten Anmeldeinformationen zur Authentifizierung

Veröffentlichen einer Anwendung in Azure oder einen vorhandenen Clouddienst überwachen, erfordert Visual Studio Anmeldeinformationen zum Authentifizieren von Anforderungen an Azure: Ihre Azure-Abonnement-ID und ein gültiges x. 509-v3-Zertifikat mit einem Schlüssel von mindestens 2048 Bits. Diese Anmeldeinformationen über eine der folgenden Methoden:

- In Visual Studio auf **Ansicht > Server-Explorer**, mit der rechten Maustaste die **Azure** Knoten **Herstellen einer Verbindung mit Microsoft Azure-Abonnement**, und melden Sie sich.
- Erstellen Sie eine Abonnementdatei (`.publishsettings`), die einen öffentlichen Schlüssel für das Zertifikat enthält. Die Abonnementdatei kann Anmeldeinformationen für mehrere Abonnements enthalten, wie in diesem Artikel beschrieben.

Hinweis: Diese Anmeldeinformationen unterscheiden sich von Anmeldeinformationen zum Authentifizieren von Anforderungen an Azure Storage-Dienste verwendet.

## <a name="create-a-subscription-file"></a>Erstellen einer Abonnementdatei

Klicken Sie im Server-Explorer mit der Maustaste der **Azure** Knoten, und wählen **Abonnements verwalten und Filtern**. Wählen Sie dann die **Zertifikate** Registerkarte, und führen Sie eine der folgenden Aktionen aus:

- Wählen Sie **Import** zum Öffnen der **Microsoft Azure-Abonnements importieren** Dialogfeld. Wählen Sie die **Abonnementdatei herunterladen** verknüpfen, und speichern Sie die heruntergeladene Datei im Browser an einen temporären Speicherort. Zurück in das Dialogfeld navigieren Sie zum Speicherort Downloads, und klicken Sie dann zur Verwendung bei der Authentifizierung importieren.
- Wählen Sie ein aktives Abonnement und **bearbeiten**, die ein Dialogfeld, in dem Sie ein vorhandenes Abonnement für die Verwendung bei der Authentifizierung bearbeiten, zu öffnen.
- Wählen Sie **neu** zum Öffnen der **neues Abonnement** Dialogfeld und geben Sie die erforderlichen Details. Zum Hochladen des Zertifikats in der Cloud-Dienst sind aufgeführt, klicken Sie im Dialogfeld melden Sie sich im Azure-Portal, navigieren Sie zu Ihrem Clouddienst **Einstellungen > Verwaltungszertifikate**Option **hochladen**, klicken Sie dann Geben Sie den Pfad zu der `.cer` Datei.

Wenn Sie ein Zertifikat selbst erstellen möchten, finden Sie die Anweisungen im [erstellen und Hochladen eines verwaltungszertifikats für Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) , und klicken Sie dann das Zertifikat manuell Hochladen der [Azure-Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Nächste Schritte

- [Allgemeine Übersicht über Web-Apps](https://docs.microsoft.com/azure/app-service/)
- [Bereitstellen Sie Ihrer app in Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Bereitstellen von WebJobs mit Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Erstellen und Bereitstellen eines Clouddiensts](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)