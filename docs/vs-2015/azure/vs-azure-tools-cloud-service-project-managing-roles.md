---
title: Verwalten von Rollen in Azure Cloud Services mit Visual Studio | Microsoft-Dokumentation
description: Informationen Sie zum Hinzufügen und Entfernen von Rollen in Azure Cloud Services mit Visual Studio.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001975"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Verwalten von Rollen in Azure Cloud Services mit Visual Studio
Nachdem Sie Ihren Azure-Cloud-Dienst erstellt haben, können Sie ihm neue Rollen hinzufügen oder vorhandene Rollen daraus entfernen. Sie können auch ein vorhandenes Projekt importieren und konvertieren Sie ihn in eine Rolle. Sie können z. B. eine ASP.NET-Webanwendung importieren und legen es als eine Webrolle.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Hinzufügen einer Rolle zu einem Azure-Cloud-Dienst
Die folgenden Schritte begleiten Sie eine Azure-Cloud-Dienstprojekt in Visual Studio eine Web- oder Workerrollen-Rolle hinzugefügt.

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, erweitern Sie den Projektknoten

1. Mit der rechten Maustaste die **Rollen** Knoten aus, um das Kontextmenü anzuzeigen. Wählen Sie im Kontextmenü des **hinzufügen**, und wählen Sie eine vorhandene Web- oder workerrolle aus der aktuellen Projektmappe, oder erstellen Sie eine Web- oder Workerrollen-Projekt. Sie können auch ein entsprechendes Projekt auswählen, wie z. B. ein ASP.NET-Webanwendungsprojekt, und es einem rollenprojekt zuordnen.

    ![Menüoptionen zum Hinzufügen einer Rolle zu einer Azure-Cloud-Dienstprojekt](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Entfernen einer Rolle von einem Azure-Cloud-Dienst
Die folgenden Schritte führen Sie durch Entfernen einer Web- oder Workerrollen-Rolle aus einer Azure-Cloud-Dienstprojekt in Visual Studio.

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, erweitern Sie den Projektknoten

1. Erweitern Sie die **Rollen** Knoten.

1. Mit der rechten Maustaste des Knotens, die Sie verwenden möchten, entfernen, und wählen Sie im Kontextmenü der **entfernen**. 

    ![Menüoptionen zum Hinzufügen einer Rolle zu einem Azure-Cloud-Dienst](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Erneutes Hinzufügen einer Rolle zu einem Azure-Cloud-Dienst-Projekt
Wenn Sie eine Rolle aus Ihrem clouddienstprojekt entfernen, aber später, um die Rolle wieder zum Projekt hinzuzufügen, werden nur die rollendeklaration und grundlegende Attribute wie Endpunkte und Diagnoseinformationen hinzugefügt. Werden keine zusätzlichen Ressourcen oder Verweise hinzugefügt, um die `ServiceDefinition.csdef` Datei oder der `ServiceConfiguration.cscfg` Datei. Wenn Sie diese Informationen hinzufügen möchten, müssen Sie es manuell wieder in diesen Dateien hinzufügen.

Beispielsweise können Sie eine webdienstrolle entfernen und später entscheiden, diese Rolle wieder in der Projektmappe hinzufügen. Wenn Sie dies tun, tritt ein Fehler auf. Um diesen Fehler zu vermeiden, müssen Sie Hinzufügen der `<LocalResources>` in wieder in der folgenden XML dargestellte-Element der `ServiceDefinition.csdef` Datei. Verwenden Sie den Namen der webdienstrolle, die Sie dem Projekt wieder hinzugefügt haben, als Teil des Namensattributs für das **<LocalStorage>** Element. In diesem Beispiel wird der Name der webdienstrolle **WCFServiceWebRole1**.

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>Nächste Schritte
- [Konfigurieren der Rollen für Azure-Clouddienst mit Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
