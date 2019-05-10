---
title: 'Vorgehensweise: Führen Sie ein SharePoint-Befehl | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f5c285e71179c5dd59fad0357dbf71ee4b32f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813888"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Vorgehensweise: Führen Sie einen SharePoint-Befehl
  Wenn Sie das Serverobjektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie erstellen eine benutzerdefinierte *SharePoint-Befehls* zum Aufrufen der API. Nachdem Sie den Befehl zu definieren und mit der SharePoint-Tools-Erweiterung bereitgestellt haben, kann die Erweiterung den Befehl in der SharePoint-Serverobjektmodell aufrufen ausführen. Um den Befehl auszuführen, verwenden Sie eine der Methoden der ExecuteCommand ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt.

 Weitere Informationen zum Zweck der SharePoint-Befehle finden Sie unter [rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Zum Ausführen eines SharePoint-Befehls

1. Erhalten Sie in der SharePoint-Tools-Erweiterung eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt. Die Möglichkeit, die Sie erhalten eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt abhängig ist, auf den Typ der Erweiterung, die Sie erstellen:

    - Verwenden Sie in einer Erweiterung der SharePoint-Projektsystem die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> Eigenschaft.

         Weitere Informationen zu Project-System-Erweiterungen, finden Sie unter [Erweitern der SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md).

    - In einer Erweiterung von der **SharePoint-Verbindungen** Knoten im **Server-Explorer**, verwenden Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> Eigenschaft. Zum Abrufen einer <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> -Objekts die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> Eigenschaft.

         Weitere Informationen zu **Server-Explorer** -Erweiterungen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - Verwenden Sie im Code, der nicht Teil einer Erweiterung der SharePoint-Tools, z. B. ein Projektvorlagen-Assistent, ist die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Eigenschaft.

         Weitere Informationen zu den Projektdienst abrufen, finden Sie unter [verwenden SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).

2. Rufen Sie eine der Methoden der ExecuteCommand der <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt. Übergeben Sie den Namen des Befehls, die Sie auf das erste Argument der Methode ExecuteCommand ausführen möchten. Wenn der Befehl einen benutzerdefinierten Parameter verfügt, übergeben Sie diesen Parameter an das zweite Argument der ExecuteCommand-Methode.

     Es gibt eine andere ExecuteCommand Überladung für jeden unterstützten Befehlssignatur. Die folgende Tabelle enthält die unterstützten Signaturen und die Überladung auf, um für jede Signatur verwenden.

    |Befehlssignatur|ExecuteCommand Überladung verwenden|
    |-----------------------|------------------------------------|
    |Der Befehl weist nur die standardmäßige <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter und keinen Wert zurückgibt.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Der Befehl weist nur die standardmäßige <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter und ein Wert zurückgegeben.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Der Befehl verfügt über zwei Parameter (die Standardeinstellung <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> und einen benutzerdefinierten Parameter) und keinen Wert zurückgibt.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Der Befehl hat zwei Parameter und ein Wert zurückgegeben.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Überladung aufrufen, die `Contoso.Commands.UpgradeSolution` -Befehl, der im beschriebene [wie: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 Die `Execute` -Methode in diesem Beispiel ist eine Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> -Methode der der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> -Schnittstelle in einem benutzerdefinierten Bereitstellungsschritt. Dieser Code im Rahmen eines größeren Beispiels, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Beachten Sie die folgenden Details über den Aufruf der <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Methode:

- Der erste Parameter gibt den Befehl, den aufgerufen werden soll. Diese Zeichenfolge mit dem Wert übereinstimmt, die Sie zum Übergeben der <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> in der Befehlsdefinition.

- Der zweite Parameter ist der Wert, den an den benutzerdefinierten zweiten Parameter des Befehls übergeben werden sollen. In diesem Fall ist der vollständige Pfad des der *.wsp* -Datei, die zur SharePoint-Website aktualisiert wird.

- Der Code übergibt die nicht den impliziten <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter an den Befehl. Dieser Parameter wird übergeben an den Befehl automatisch, wenn Sie den Befehl über eine Erweiterung der SharePoint-Projektsystem oder eine Erweiterung von Aufrufen der **SharePoint-Verbindungen** Knoten **Server-Explorer**. In anderen Typen von Projektmappen, z. B. in einem Projekt-Assistenten, die implementiert die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> -Schnittstelle, die dieser Parameter ist **null**.

## <a name="compile-the-code"></a>Kompilieren des Codes
 In diesem Beispiel erfordert einen Verweis auf der Microsoft.VisualStudio.SharePoint-Assembly.

## <a name="see-also"></a>Siehe auch
- [Rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
