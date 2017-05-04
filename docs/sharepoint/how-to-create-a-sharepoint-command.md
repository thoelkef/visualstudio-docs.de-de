---
title: "How to: Create a SharePoint Command | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  Wenn Sie das Serverobjektmodell in einer SharePoint\-Tools\-Erweiterung verwenden möchten, müssen Sie einen benutzerdefinierten *SharePoint\-Befehl* erstellen, um die API aufzurufen.  Sie definieren den SharePoint\-Befehl in einer Assembly, die direkte Aufrufe des Serverobjektmodells ausführen kann.  
  
 Weitere Informationen über den Zweck von SharePoint\-Befehlen finden Sie [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### So erstellen Sie einen SharePoint\-Befehl  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt mit der folgenden Konfiguration:  
  
    -   Zielt auf .NET Framework, Version 3.5, ab.  Weitere Informationen zur Auswahl des Zielframeworks finden Sie unter [Gewusst wie: .NET Framework-Version als Ziel](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Zielt auf die AnyCPU\- oder x64\-Plattform ab.  Standardmäßig ist die Zielplattform für Klassenbibliotheksprojekte AnyCPU.  Weitere Informationen zur Auswahl der Zielplattform finden Sie unter [NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/de-de/294a75d2-4279-4b72-8298-2bea05be907a).  
  
    > [!NOTE]  
    >  Sie können keinen SharePoint\-Befehl in einem Projekt implementieren, das eine SharePoint\-Tools\-Erweiterung definiert, da SharePoint\-Befehle auf .NET Framework 3.5 und SharePoint\-Tools\-Erweiterungen auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] abzielen.  Sie müssen alle SharePoint\-Befehle definieren, die von der Erweiterung in einem separaten Projekt verwendet werden.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Erstellen Sie in einer Klasse im Projekt eine Methode, durch die der SharePoint\-Befehl definiert wird.  Die Methode muss den folgenden Richtlinien entsprechen:  
  
    -   Sie darf über einen oder zwei Parameter verfügen.  
  
         Der erste Parameter muss ein <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>\-Objekt sein.  Dieses Objekt stellt den Microsoft.SharePoint.SPSite oder Microsoft.SharePoint.SPWeb bereit, in dem der Befehl ausgeführt wird.  Sie stellt auch ein <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>\-Objekt bereit, das zum Schreiben von Meldungen in den Fenstern **Ausgabe** oder **Fehlerliste** in Visual Studio verwendet werden kann.  
  
         Der zweite Parameter kann ein beliebiger Typ sein. Dieser Parameter ist optional.  Sie können dem SharePoint\-Befehl diesen Parameter hinzufügen, wenn Daten von der SharePoint\-Tools\-Erweiterung an den Befehl weitergegeben werden müssen.  
  
    -   Optional kann ein Rückgabewert festgelegt werden.  
  
    -   Der zweite Parameter und der Rückgabewert müssen einen Typ aufweisen, der von Windows Communication Foundation \(WCF\) serialisiert werden kann.  Weitere Informationen finden Sie unter [Vom Datenvertragsserialisierer unterstützte Typen](http://msdn.microsoft.com/library/7381b200-437a-4506-9556-d77bf1bc3f34) und [Verwenden der XmlSerializer-Klasse](http://msdn.microsoft.com/library/c680602d-39d3-44f1-bf22-8e6654ad5069).  
  
    -   Die Methode kann über jede Sichtbarkeit \(**public**, **internal** oder **private**\) verfügen und kann statisch oder nicht statisch sein.  
  
4.  Wenden Sie den <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> auf die Methode an.  Dieses Attribut gibt einen eindeutigen Bezeichner für den Befehl an. Dieser Bezeichner muss nicht mit dem tatsächlichen Methodennamen übereinstimmen.  
  
     Der gleiche eindeutige Bezeichner muss angegeben werden, wenn der Befehl von der SharePoint\-Tools\-Erweiterung aufgerufen werden soll.  Weitere Informationen erhalten Sie unter [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein SharePoint\-Befehl mit dem Bezeichner `Contoso.Commands.UpgradeSolution` veranschaulicht.  Dieser Befehl verwendet APIs im Serverobjektmodell, um ein Upgrade auf eine bereitgestellte Lösung auszuführen.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 Zusätzlich zum impliziten ersten <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>\-Parameter verfügt dieser Befehl auch über einen benutzerdefinierten Zeichenfolgenparameter, der den vollständigen Pfad der WSP\-Datei enthält, mit dem die SharePoint\-Website aktualisiert wird.  Unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) wird dieser Code noch einmal in einem umfassenderen Beispiel verwendet.  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## Bereitstellen des Befehls  
 Zum Bereitstellen des Befehls integrieren Sie die Befehlsassembly in das [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket mit der Erweiterungsassembly, die den Befehl verwendet.  Sie müssen auch einen Eintrag für die Befehlsassembly in der Datei "extension.vsixmanifest" hinzufügen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  