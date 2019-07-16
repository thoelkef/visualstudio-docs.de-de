---
title: Publish-WebApplicationVM | Microsoft Docs
description: Erfahren Sie, wie eine Webanwendung auf einem virtuellen Computer bereitgestellt wird. Dieses Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie noch nicht vorhanden sind.
author: ghogen
manager: jillfra
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e35f5decee2a908a9d1075ff3f6365a1d358c7b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957527"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell-Skript)
Stellt eine Webanwendung auf einem virtuellen Computer bereit. Das Skript erstellt die erforderlichen Ressourcen in Ihrem Azure-Abonnement, wenn sie noch nicht vorhanden sind.

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
Der Pfad zur JSON-Konfigurationsdatei, in der die Details der Bereitstellung beschrieben sind.

| Aliase | Keine |
| --- | --- |
| Erforderlich? |true |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

### <a name="subscriptionname"></a>SubscriptionName
Der Name des Azure-Abonnements, in dem Sie den virtuellen Computer erstellen möchten.

| Aliase | Keine |
| --- | --- |
| Erforderlich? |False |
| Position |benannt |
| Standardwert |Verwendet das erste Abonnement in der Abonnementdatei. |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Der Pfad zum Webbereitstellungspaket für die Veröffentlichung auf dem virtuellen Computer. Sie können dieses Paket in Visual Studio mithilfe des Assistenten "Web veröffentlichen" erstellen. Weitere Informationen finden Sie unter [How to: Create a Web Deployment Package in Visual Studio (Vorgehensweise: Erstellen eines Webbereitstellungspaket in Visual Studio)](https://msdn.microsoft.com/library/dd465323.aspx).

| Aliase | Keine |
| --- | --- |
| Erforderlich? |False |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Bei „true“ können Zertifikate verwendet werden, die nicht von einer vertrauenswürdigen Zertifizierungsstelle signiert sind.

| Aliase | Keine |
| --- | --- |
| Erforderlich? |False |
| Position |benannt |
| Standardwert |False |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

### <a name="vmpassword"></a>VMPassword
Die Anmeldeinformationen für das Konto des virtuellen Computers. Beispiel: -VMPassword @{Name = "admin"; Password = "password"}

| Aliase | Keine |
| --- | --- |
| Erforderlich? |False |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Die Anmeldeinformationen für die SQL-Datenbank in Azure. Beispiel: -DatabaseServerPassword @{Name = "admin"; Password = "password"}

| Aliase | Keine |
| --- | --- |
| Erforderlich? |False |
| Position |benannt |
| Standardwert |Keine |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Falls "true", werden Nachrichten vom Skript in den Ausgabedatenstrom ausgegeben.

| Aliase | Keine |
| --- | --- |
| Erforderlich? |False |
| Position |benannt |
| Standardwert |False |
| Pipelineeingabe akzeptieren? |False |
| Platzhalterzeichen akzeptieren? |False |

## <a name="remarks"></a>Anmerkungen
Eine ausführliche Erläuterung der Verwendung des Skripts zum Erstellen von Entwicklungs- und Testumgebungen finden Sie unter [Verwenden von Windows PowerShell-Skripts zum Veröffentlichen in Entwicklungs- und Testumgebungen](vs-azure-tools-publishing-using-powershell-scripts.md).

In der JSON-Konfigurationsdatei sind die Details angegeben, was bereitgestellt werden muss. Dazu zählen die Informationen, die Sie beim Erstellen des Projekts angegeben haben, z. B. der Name, die Affinitätsgruppe, das VHD-Image und die Größe des virtuellen Computers. Dazu zählen außerdem die Endpunkte auf dem virtuellen Computer, die Datenbanken, die bereitgestellt werden sollen, und Webbereitstellungsparameter. Der folgende Code zeigt ein Beispiel einer JSON-Konfigurationsdatei:

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

Sie können die JSON-Konfigurationsdatei bearbeiten, um die Elemente zu ändern, die bereitgestellt werden. Ein virtueller Computer und ein Clouddienst sind erforderlich, aber der Datenbankabschnitt ist optional.
