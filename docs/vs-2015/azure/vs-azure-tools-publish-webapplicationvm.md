---
title: Publish-Webapplicationwebsite | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Webanwendung mit einem virtuellen Computer bereitstellen. Dieses Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie nicht vorhanden sind.
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002044"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (Windows PowerShell-Skript)
Stellt eine Webanwendung mit einem virtuellen Computer bereit. Das Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie nicht vorhanden sind.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Konfiguration
Der Pfad zur JSON-Konfigurationsdatei, die die Details der Bereitstellung beschreibt.

| Aliase | none |
| --- | --- |
| Erforderlich? |true |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

### <a name="subscriptionname"></a>Abonnementname
Der Name des Azure-Abonnements in der Sie den virtuellen Computer erstellen möchten.

| Aliase | none |
| --- | --- |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |Verwendet das erste Abonnement in der Abonnementdatei. |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Der Pfad zum Webbereitstellungspaket, auf dem virtuellen Computer zu veröffentlichen. Sie können dieses Paket mithilfe des Assistenten für Webveröffentlichung in Visual Studio erstellen. Finden Sie unter [Vorgehensweise: erstellen ein Webbereitstellungspakets in Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Aliase | none |
| --- | --- |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Bei "true", können Sie die Verwendung von Zertifikaten, die nicht von einer vertrauenswürdigen Stammzertifizierungsstelle signiert.

| Aliase | none |
| --- | --- |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |False |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

### <a name="vmpassword"></a>VMPassword
Die Anmeldeinformationen für das Konto des virtuellen Computers. Beispiel: - VMPassword @{Name = "Admin"; Kennwort = "Password"}

| Aliase | none |
| --- | --- |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Die Anmeldeinformationen für die SQL-Datenbank in Azure. Beispiel: - DatabaseServerPassword @{Name = "Admin"; Kennwort = "Password"}

| Aliase | none |
| --- | --- |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |none |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True gibt an, Nachrichten Drucken aus dem Skript, in den Ausgabestream.

| Aliase | none |
| --- | --- |
| Erforderlich? |False |
| Position |Benannt |
| Standardwert |False |
| Akzeptieren Pipelineeingabe? |False |
| Akzeptieren Platzhalterzeichen? |False |

## <a name="remarks"></a>Hinweise
Eine vollständige Erklärung der Vorgehensweise zur Verwendung des Skripts erstellen Entwicklungs- und testumgebungen, finden Sie unter [mithilfe von Windows PowerShell-Skripts zum Veröffentlichen in Entwicklungs- und Testumgebungen](vs-azure-tools-publishing-using-powershell-scripts.md).

Die JSON-Konfigurationsdatei gibt Details zu bereitgestellt werden. Sie enthält die Informationen, die Sie beim Erstellen des Projekts, wie der Name, die Affinitätsgruppe, die VHD-Image und die Größe des virtuellen Computers angegeben haben. Außerdem enthält die Endpunkte auf dem virtuellen Computer, die Datenbanken, die bereitgestellt, sofern vorhanden, und webbereitstellungsparameter. Der folgende Code zeigt eine Beispiel für JSON-Konfigurationsdatei:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Sie können die JSON-Konfigurationsdatei zum Ändern, was bereitgestellt wird, bearbeiten. Ein virtueller Computer und Cloud-Dienst erforderlich sind, aber der Datenbankabschnitt ist optional.

