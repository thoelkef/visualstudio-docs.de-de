---
title: 'Vorgehensweise: Erstellen eines SharePoint-Befehls | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], creating
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 913ccb36c54914387cd6ca8a50a350ada1b14ce7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-command"></a>Gewusst wie: Erstellen eines SharePoint-Befehls
  Wenn Sie das Serverobjektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie eine benutzerdefinierte erstellen *SharePoint-Befehl* zum Aufrufen der API. Sie definieren den SharePoint-Befehl in einer Assembly, die direkt in das Serverobjektmodell aufrufen kann.  
  
 Weitere Informationen zum Zweck der SharePoint-Befehlen finden Sie unter [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>So erstellen Sie einen SharePoint-Befehl  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt, das die folgende Konfiguration aufweist:  
  
    -   .NET Framework 3.5 abzielt. Weitere Informationen zum Auswählen des Zielframeworks finden Sie unter [wie: eine Version von .NET Framework als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Das Ziel ist die "anycpu" oder X64 Plattform. Standardmäßig ist die Zielplattform für Klassenbibliotheksprojekte "anycpu". Weitere Informationen zum Auswählen der Zielplattform finden Sie unter [Vorgehensweise: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Sie können einen SharePoint-Befehl im selben Projekt, das eine SharePoint-Tools-Erweiterung definiert implementieren, da SharePoint-Befehle die .NET Framework 3.5 und SharePoint-Tools-Erweiterungen abzielen die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Sie müssen alle SharePoint-Befehle definieren, die von der Erweiterung in einem separaten Projekt verwendet werden. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Erstellen Sie in einer Klasse im Projekt eine Methode, die Ihre SharePoint-Befehl definiert. Die Methode muss die folgenden Richtlinien entsprechen:  
  
    -   Sie können ein oder zwei Parameter aufweisen.  
  
         Der erste Parameter muss ein <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Objekt. Dieses Objekt enthält die Microsoft.SharePoint.SPSite oder Microsoft.SharePoint.SPWeb, in dem der Befehl ausgeführt wird. Sie bietet außerdem eine <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> -Objekt, das zum Schreiben von Nachrichten verwendet werden kann die **Ausgabe** Fenster oder **Fehlerliste** Fenster in Visual Studio.  
  
         Der zweite Parameter kann einen Typ Ihrer Wahl sein, aber dieser Parameter ist optional. Wenn Sie Daten aus der SharePoint-Tools-Erweiterung an den Befehl übergeben müssen, können Sie diesen Parameter auf den SharePoint-Befehl hinzufügen.  
  
    -   Sie können einen Rückgabewert haben, aber dies ist optional.  
  
    -   Der zweite Parameter und Rückgabetypen-Wert muss ein Typ sein, der von der Windows Communication Foundation (WCF) serialisiert werden können. Weitere Informationen finden Sie unter [Typen unterstützt, durch den Datenvertragsserialisierer](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) und [verwenden der XmlSerializer-Klasse](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Die Methode kann eine beliebige Sichtbarkeit aufweisen (**öffentlichen**, **interne**, oder **private**), und es kann statisch oder nicht statisch sein.  
  
4.  Anwenden der <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> an die Methode. Dieses Attribut gibt einen eindeutigen Bezeichner für den Befehl an. Dieser Bezeichner muss nicht in den Methodennamen übereinstimmen.  
  
     Wenn Sie den Befehl aus der SharePoint-Tools-Erweiterung aufrufen, müssen Sie den gleichen Bezeichner angeben. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen eines SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, einen SharePoint-Befehl mit dem Bezeichner `Contoso.Commands.UpgradeSolution`. Dieser Befehl verwendet die APIs in das Serverobjektmodell auf einer bereitgestellten Lösung aktualisieren.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Zusätzlich zu den impliziten ersten <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Parameter mit diesem Befehl auch hat einen benutzerdefinierte Zeichenfolgenparameter, der den vollständigen Pfad der WSP-Datei enthält, die auf der SharePoint-Website aktualisiert wird. Um diesen Code im Rahmen eines umfangreicheren Beispiels sehen zu können, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>Bereitstellen des Befehls  
 Zum Bereitstellen des Befehls den Befehlsassembly in der gleichen einschließen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, mit der Erweiterungsassembly, die der Befehl verwendet. Sie müssen auch einen Eintrag für die Befehlsassembly in der Datei "Extension.vsixmanifest" hinzufügen. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Vorgehensweise: Ausführen eines SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Exemplarische Vorgehensweise: Erweitern des Server-Explorers für die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  