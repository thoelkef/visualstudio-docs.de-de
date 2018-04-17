---
title: 'Vorgehensweise: Ausführen eines SharePoint-Befehls | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 824a747d9253817e1f188730996dac707b3e5ee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-execute-a-sharepoint-command"></a>Gewusst wie: Ausführen eines SharePoint-Befehls
  Wenn Sie das Serverobjektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie eine benutzerdefinierte erstellen *SharePoint-Befehl* zum Aufrufen der API. Nachdem Sie den Befehl zu definieren und mit der SharePoint-Tools-Erweiterung bereitgestellt haben, kann die Erweiterung der Befehl in der SharePoint-Serverobjektmodell aufrufen ausgeführt. Um den Befehl auszuführen, verwenden Sie eine der Methoden von "ExecuteCommand" ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt.  
  
 Weitere Informationen zum Zweck der SharePoint-Befehlen finden Sie unter [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Zum Ausführen eines SharePoint-Befehls  
  
1.  In der SharePoint-Tools-Erweiterung Abrufen einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt. Die Möglichkeit, die Sie erhalten eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt abhängig ist, auf den Typ der Erweiterung, die Sie erstellen:  
  
    -   Verwenden Sie eine Erweiterung der SharePoint-Projektsystem, die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> Eigenschaft.  
  
         Weitere Informationen zum Project-System-Erweiterungen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   In einer Erweiterung des der **SharePoint-Verbindungen** Knoten **Server-Explorer**, verwenden Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> Eigenschaft. Zum Abrufen einer <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> -Objekts die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> Eigenschaft.  
  
         Weitere Informationen zu **Server-Explorer** -Erweiterungen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Verwenden Sie im Code, der nicht Teil einer Erweiterung der SharePoint-Tools, z. B. ein Projekt Vorlagen-Assistenten ist die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Eigenschaft.  
  
         Weitere Informationen zum Abrufen von Project-Dienst finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Rufen Sie eine der Methoden "ExecuteCommand" von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt. Übergeben Sie den Namen des Befehls, der auf das erste Argument der Methode "ExecuteCommand" ausgeführt werden soll. Wenn der Befehl einen benutzerdefinierten Parameter verfügt, übergeben Sie diesen Parameter an das zweite Argument der Methode "ExecuteCommand" ein.  
  
     Es wird eine andere Überladung für "ExecuteCommand" für jede unterstützte Befehlssignatur. Die folgende Tabelle enthält die unterstützten Signaturen und die Überladung auf, um für jede Signatur verwenden.  
  
    |Befehlssignatur|"ExecuteCommand" Überladung verwenden|  
    |-----------------------|------------------------------------|  
    |Der Befehl hat nur die standardmäßige <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter und keinen Wert zurückgibt.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Der Befehl hat nur die standardmäßige <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter sowie einen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Der Befehl verfügt über zwei Parameter (die Standardeinstellung <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> und einen benutzerdefinierten Parameter) und keinen Wert zurückgibt.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Der Befehl verfügt über zwei Parameter und einen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Überladung aufrufen, die `Contoso.Commands.UpgradeSolution` -Befehl, der im beschriebene [wie: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 Die `Execute` in diesem Beispiel gezeigten Methode ist eine Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> Methode der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> Schnittstelle in einem Schritt benutzerdefinierte Bereitstellung. Um diesen Code im Rahmen eines umfangreicheren Beispiels sehen zu können, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Beachten Sie die folgenden Informationen zu den Aufruf der <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Methode:  
  
-   Der erste Parameter gibt den Befehl, den aufgerufen werden soll. Diese Zeichenfolge mit dem Wert übereinstimmt, die Sie zum Übergeben der <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> auf der Befehlsdefinition.  
  
-   Der zweite Parameter ist der Wert, den an den benutzerdefinierten zweiten Parameter des Befehls übergeben werden sollen. In diesem Fall ist es sich um den vollständigen Pfad der WSP-Datei, die auf der SharePoint-Website aktualisiert wird.  
  
-   Der Code übergibt keine impliziter <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter an den Befehl. Dieser Parameter wird der Befehl automatisch beim Aufrufen des Befehls aus einer Erweiterung der SharePoint-Projektsystem oder eine Erweiterung des übergeben der **SharePoint-Verbindungen** Knoten **Server-Explorer**. In anderen Arten von Projektmappen, z. B. in einem Projekt-Assistenten, die implementiert die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> -Schnittstelle, die dieser Parameter ist **null**.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert einen Verweis auf die Microsoft.VisualStudio.SharePoint-Assembly.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Exemplarische Vorgehensweise: Erweitern des Server-Explorers für die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  