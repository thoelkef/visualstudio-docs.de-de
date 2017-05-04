---
title: "Overview of the Programming Model of SharePoint Tools Extensions | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "SharePoint development in Visual Studio, extensibility object models"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Overview of the Programming Model of SharePoint Tools Extensions
  Wenn Sie eine Erweiterung für die SharePoint\-Tools in Visual Studio erstellen, beginnen Sie damit, indem Sie eine oder mehrere Erweiterungsschnittstellen implementieren, die von den SharePoint\-Tools verfügbar gemacht werden.  In den meisten Fällen verwenden Sie auch andere von den SharePoint\-Tools bereitgestellte Typen, um Features in der Erweiterung zu implementieren.  Für einige Szenarien können Sie auch Typen in anderen Objektmodellen verwenden, die von Visual Studio und SharePoint bereitgestellt werden.  Sie müssen den Zweck der einzelnen Objektmodelle verstehen und wissen, wie Sie diese miteinander kombinieren können, um Erweiterungen für die SharePoint\-Tools zu erstellen.  
  
## Erweitern der SharePoint\-Tools durch das Implementieren von Erweiterungsschnittstellen  
 Visual Studio verwendet das Managed Extensibility Framework \(MEF\) in .NET Framework 4 zum Bereitstellen des Erweiterungsmodells für die SharePoint\-Tools.  MEF ist eine API \(implementiert in der System.ComponentModel.Compositions\-Assembly\), die Anwendungen ermöglicht, Erweiterungspunkte verfügbar zu machen und Erweiterungen zur Laufzeit zu ermitteln und zu laden.  Weitere Informationen über MEF finden Sie unter [Managed Extensibility Framework &#40;MEF&#41;](../Topic/Managed%20Extensibility%20Framework%20(MEF).md).  
  
 Um die SharePoint\-Tools zu erweitern, implementieren Sie eine oder mehrere Erweiterungsschnittstellen, die von Visual Studio bereitgestellt werden.  Sie müssen auch das <xref:System.ComponentModel.Composition.ExportAttribute> sowie bei Bedarf weitere für die SharePoint\-Tools spezifische Attribute auf Ihre Schnittstellenimplementierung anwenden.  In der folgenden Tabelle sind die Schnittstellen aufgeführt, die Sie zum Erweitern der SharePoint\-Tools implementieren können.  
  
|Schnittstelle|Beschreibung|  
|-------------------|------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementieren Sie diese Schnittstelle, um einen neuen Typ von SharePoint\-Projektelement zu definieren.  Ein Beispiel finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementieren Sie diese Schnittstelle, um einen SharePoint\-Projektelementtyp zu erweitern, der in Visual Studio bereits installiert ist.  Ein Beispiel finden Sie unter [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementieren Sie diese Schnittstelle, um SharePoint\-Projekte zu erweitern.  Ein Beispiel finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementieren Sie diese Schnittstelle, um einen neuen Bereitstellungsschritt zu definieren, der beim Bereitstellen oder Zurückziehen eines SharePoint\-Projektelements ausgeführt werden kann.  Ein Beispiel finden Sie unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementieren Sie diese Schnittstelle, um einen vorhandenen Knoten unter dem Knoten **SharePoint\-Verbindungen** im Fenster **Server\-Explorer** zu erweitern.  Ein Beispiel finden Sie unter: [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementieren Sie diese Schnittstelle, um einen neuen Knotentyp unter dem Knoten **SharePoint\-Verbindungen** im Fenster **Server\-Explorer** zu definieren.  Ein Beispiel finden Sie unter: [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementieren Sie diese Schnittstelle, um eine benutzerdefinierte Funktionsvalidierungsregel zu definieren.  Ein Beispiel finden Sie unter [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementieren Sie diese Schnittstelle, um eine benutzerdefinierte Paketvalidierungsregel zu definieren.  Ein Beispiel finden Sie unter [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 Nachdem Sie eine Erweiterung der SharePoint\-Tools implementiert haben, müssen Sie die Erweiterungsassembly in einem Visual Studio\-Erweiterungspaket \(VSIX\) bereitstellen, damit Visual Studio die Erweiterung ermitteln und laden kann.  Weitere Informationen finden Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Grundlegendes zu den Objektmodellen, die Sie in Erweiterungen für SharePoint\-Tools verwenden  
 Es gibt verschiedene Objektmodelle, die Sie beim Erstellen von Erweiterungen für die SharePoint\-Tools verwenden können:  
  
-   *Objektmodell der SharePoint\-Tools*:  Dieses Objektmodell stellt die Erweiterungsschnittstellen bereit, die Sie zum Erstellen von SharePoint\-Tools\-Erweiterungen und anderen verwandten Typen implementieren.  
  
-   *Automatisierungs\- und Integrationsobjektmodelle von Visual Studio*:  Verwenden Sie diesen Objektmodelle, um auf Visual Studio\-Funktionen zuzugreifen, die nicht im Bereich des Objektmodells der SharePoint\-Tools liegen.  
  
    > [!NOTE]  
    >  Mit dem SharePoint\-Projektdienst können Sie einige Objekte des SharePoint\-Tools\-Objektmodells in Automatisierungs\- und Integratonsobjektmodelle von Visual Studio konvertieren und umgekehrt.  Weitere Informationen finden Sie unter [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Server\- und Clientobjektmodelle von SharePoint*:  Mit diesen Objektmodellen können Sie eine SharePoint\-Website ändern oder Daten aus einer SharePoint\-Website im Kontext einer SharePoint\-Tools\-Erweiterung abrufen.  
  
### Objektmodell der SharePoint\-Tools  
 In jeder SharePoint\-Tools\-Erweiterung werden mit Typen im SharePoint\-Tools\-Objektmodell das Kernverhalten und die Kernfunktionen der Erweiterung definiert.  In der folgenden Tabelle werden die Namespaces beschrieben, die in diesem Objektmodell enthalten sind.  
  
|Assembly|Namespace|Beschreibung|  
|--------------|---------------|------------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Enthält Typen, mit denen Sie das SharePoint\-Projektsystem erweitern und automatisieren können.  Sie können z. B. die integrierten SharePoint\-Projekte und \-Projektelemente erweitern, oder Sie können eigene Projektelemente erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Enthält Typen, mit denen Sie den Bereitstellungsprozess für SharePoint\-Projekte erweitern können, beispielsweise durch Erstellen eigener Bereitstellungsschritte und Bereitstellungskonfigurationen.  Weitere Informationen finden Sie unter [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Enthält Typen, mit denen Sie Knoten unter dem Knoten **SharePoint\-Verbindungen** im Fenster **Server\-Explorer** erweitern oder neue Knotentypen definieren können.  Weitere Informationen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Enthält Typen, mit denen Sie in einem SharePoint\-Projekt auf die Definition von Funktionen zugreifen können.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Enthält Typen, mit denen Sie auf die Paketdefinition in einer SharePoint\-Lösung zugreifen können.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Enthält Typen, mit denen Sie das Funktions\- und Paketvalidierungsverhalten für SharePoint\-Projekte anpassen können.  Weitere Informationen finden Sie unter [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Enthält Typen, mit denen Sie benutzerdefinierte *SharePoint\-Befehle* erstellen können.  Ein SharePoint\-Befehl ist eine Methode, die einen Aufruf in das SharePoint\-Serverobjektmodell von einer SharePoint\-Tools\-Erweiterung aus durchführt.  Weitere Informationen finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Enthält Typen, mit denen Sie Informationen zu integrierten **Server\-Explorer**\-Knoten abrufen können, die einzelne Komponenten in einer SharePoint\-Website darstellen, z. B. ein Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt.  Weitere Informationen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### Visual Studio\-Automatisierungsobjektmodell  
 Das Automatisierungsobjektmodell von Visual Studio stellt APIs bereit, mit denen Sie Visual Studio\-Projekte und die IDE automatisieren können.  Führen Sie projektbezogene Aufgaben, die nicht spezifisch für SharePoint\-Projekte sind, oder andere allgemeine Automatisierungsaufgaben in Visual Studio mit diesem Visual Studio\-Objektmodell aus.  Dieses Objektmodell wird in der Regel häufig in Visual Studio\-Add\-Ins und \-Makros verwendet, Sie können es aber auch in SharePoint\-Tools\-Erweiterungen verwenden.  
  
 Der Hauptteil des Visual Studio\-Automatisierungsobjektmodells ist in der EnvDTE.dll\-Assembly definiert.  Zusätzliche Funktionalität, die in Visual Studio 2005, Visual Studio 2008 und Visual Studio 2010 bzw. [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] eingeführt wurde, wird durch die Assemblys „EnvDTE80.dll“, „EnvDTE90.dll“ und „EnvDTE100.dll“ bereitgestellt.  Diese Assemblys sind in Visual Studio enthalten.  
  
 Weitere Informationen zum Automatisierungsobjektmodell finden Sie unter [Erweitern der Visual Studio-Umgebung](../Topic/Extending%20the%20Visual%20Studio%20Environment.md) und [Referenz zur Automatisierung und Erweiterbarkeit](../Topic/Automation%20and%20Extensibility%20Reference.md).  
  
### Visual Studio\-Integrationsobjektmodell  
 Das Integrationsobjektmodell stellt APIs bereit, mit denen Sie durch das Erstellen eines *VSPackages* Visual Studio\-Funktionen hinzufügen können.  Ein VSPackage ist ein Modul, das die Visual Studio\-IDE durch benutzerdefinierte Funktionen wie Toolfenster, Editoren, Designer, Dienste und Projekte erweitert.  
  
 Sie können das Integrationsobjektmodell verwenden, wenn Sie eine neue Visual Studio\-Funktion hinzufügen möchten, die zusammen mit den integrierten SharePoint\-Tools verwendet wird.  Wenn Sie z. B. ein benutzerdefiniertes SharePoint\-Projektelement erstellen, das eine benutzerdefinierte Aktion für eine SharePoint\-Website darstellt, können Sie auch ein VSPackage erstellen, das einen Designer für die benutzerdefinierte Aktion implementiert.  Sie können die benutzerdefinierten Aktion dem Designer zuordnen, indem Sie dem Projektelement, das die benutzerdefinierte Aktion darstellt, im **Projektmappen\-Explorer** ein Kontextmenüelement hinzufügen.  Sie können den Designer öffnen, indem Sie das Kontextmenü öffnen. \(Klicken Sie hierzu entweder mit der rechten Maustaste auf das benutzerdefinierte Aktionsprojektelement, oder wählen Sie es aus, und drücken Sie dann die UMSCHALT\+F10\-Taste.\) Wählen Sie anschließend die Option **Öffnen**.  
  
 Dieses Objektmodell ist in einem Satz mehrerer Assemblys definiert, die im Visual Studio\-SDK enthalten sind.  Einige der Hauptassemblys in diesem Objektmodell sind „Microsoft.VisualStudio.Shell.dll“, „Microsoft.VisualStudio.Shell.Interop.dll“ und „Microsoft.VisualStudio.OLE.Interop.dll“.  
  
 Weitere Informationen zum Integrationsobjektmodell finden Sie unter [Architektur der Visual Studio-Erweiterbarkeit](/visual-cpp/misc/visual-studio-extensibility-architecture) und [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md).  
  
### SharePoint\-Objektmodelle  
 SharePoint\-Tools\-Erweiterungen können SharePoint\-APIs verwenden, um eine SharePoint\-Website zu ändern oder Daten von einer SharePoint\-Website abzurufen.  [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] stellen zwei unterschiedliche Objektmodelle bereit: ein Serverobjektmodell und ein Clientobjektmodell.  
  
 Sie können APIs aus beiden Objektmodellen in einer SharePoint\-Tools\-Erweiterung verwenden. Beide Objektmodelle haben jedoch bestimmte Vor\- und Nachteile im Kontext der SharePoint\-Tools\-Erweiterungen.  Weitere Informationen finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Objektmodell|Beschreibung|  
|------------------|------------------|  
|Serverobjektmodell|Das Serverobjektmodell bietet Zugriff auf alle Funktionen, die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programmgesteuert verfügbar machen.  Dieses Objektmodell wurde für SharePoint\-Lösungen entworfen, die auf dem SharePoint\-Server ausgeführt werden.  Die Großteil dieses Objektmodells ist in der Microsoft.SharePoint.dll\-Assembly definiert.  Weitere Informationen zum Serverobjektmodell finden Sie unter [Verwenden des serverseitigen Objektmodells von SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Clientobjektmodell|Das Clientobjektmodell ist eine Teilmenge des Serverobjektmodells und kann verwendet werden, um die SharePoint\-Daten auf einem Remoteclient oder einem Server zu verarbeiten.  Beim Entwurf wurde darauf geachtet, die Anzahl der Roundtrips zu minimieren, die zum Ausführen häufiger Aufgaben notwendig ist.  Die Großteil des Clientobjektmodells ist in der Microsoft.SharePoint.Client.dll\-Assembly und der Microsoft.SharePoint.Client.Runtime.dll\-Assembly definiert.  Weitere Informationen zum Clientobjektmodell finden Sie unter [Verwaltetes Clientobjektmodell](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## Siehe auch  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)  
  
  