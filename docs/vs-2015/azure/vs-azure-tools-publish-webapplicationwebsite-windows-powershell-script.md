---
title: Publish-WebApplicationWebSite (Windows PowerShell-Skript) | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Webprojekt in eine Azure-Website veröffentlichen. Dieses Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie nicht vorhanden sind.
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001978"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell-Skript)
## <a name="syntax"></a>Syntax
Veröffentlicht ein Webprojekt auf einer Azure-Website. Das Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie nicht vorhanden sind.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Konfiguration
Der Pfad zur JSON-Konfigurationsdatei, die die Details der Bereitstellung beschreibt.

| Parameter | Standardwert |
| --- | --- |
| Aliase |none |
| Erforderlich? |true |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

## <a name="subscriptionname"></a>Abonnementname
Der Name des Azure-Abonnements, die Sie die Website erstellen möchten.

| Parameter | Standardwert |
| --- | --- |
| Aliase |none |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Der Pfad zum Webbereitstellungspaket auf der Website veröffentlichen. Sie können dieses Paket mithilfe des Assistenten für Webveröffentlichung in Visual Studio erstellen. Weitere Informationen finden Sie unter [erste Schritte mit Azure Cloud Services und ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Parameter | Standardwert |
| --- | --- |
| Aliase |none |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Benutzername und Kennwort für die SQL-Datenbank in Azure.

| Parameter | Standardwert |
| --- | --- |
| Aliase |none |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True gibt an, Nachrichten Drucken aus dem Skript, in den Ausgabestream.

| Parameter | Standardwert |
| --- | --- |
| Aliase |none |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |False |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

## <a name="remarks"></a>Hinweise
Eine vollständige Erklärung der Vorgehensweise zur Verwendung des Skripts erstellen Entwicklungs- und testumgebungen, finden Sie unter [mithilfe von Windows PowerShell-Skripts zum Veröffentlichen in Entwicklungs- und Testumgebungen](vs-azure-tools-publishing-using-powershell-scripts.md).

Die JSON-Konfigurationsdatei gibt Details zu bereitgestellt werden. Es enthält Informationen, die Sie beim Erstellen des Projekts, z.B. den Namen und den Benutzernamen für die Website angegeben werden. Darüber hinaus die bereitzustellende Datenbank, sofern vorhanden. Der folgende Code zeigt eine Beispiel für JSON-Konfigurationsdatei:

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

Sie können die JSON-Konfigurationsdatei zum Ändern der Umfang der Bereitstellung bearbeiten. Ein Abschnitt "WebSite" ist erforderlich, aber der Datenbankabschnitt ist optional.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie unter [Publish-Webapplicationwebsite (Windows PowerShell-Skript)](vs-azure-tools-publish-webapplicationvm.md)

