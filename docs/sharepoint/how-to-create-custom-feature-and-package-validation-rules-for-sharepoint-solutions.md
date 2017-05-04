---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  Zum Überprüfen des von Visual Studio generierten Lösungspakets können benutzerdefinierte Validierungsregeln erstellt werden.  Sie können eine umfassende Validierung einer vollständigen Funktion oder eines vollständigen Pakets ausführen, indem Sie im Paket\-Explorer im Kontextmenü einer Funktion oder eines Pakets die Option **Überprüfen** auswählen.  Eine Teilvalidierung wird ausgeführt, wenn Sie dem Projekt neue SharePoint\-Projektelemente oder \-Funktionen hinzufügen, um zu ermitteln, ob das Paket oder die Funktion einen gültigen Zustand aufweist.  
  
### So erstellen Sie eine benutzerdefinierte Paketvalidierungsregel  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, von der eine der folgenden Schnittstellen implementiert wird:  
  
    -   Implementieren Sie zum Erstellen einer Paketvalidierungsregel die <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>\-Schnittstelle.  
  
    -   Implementieren Sie zum Erstellen einer Funktionsvalidierungsregel die <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>\-Schnittstelle.  
  
4.  Fügen Sie der Klasse <xref:System.ComponentModel.Composition.ExportAttribute> hinzu.  Anhand dieses Attributs kann die Validierungsregel von Visual Studio erkannt und geladen werden.  Übergeben Sie den <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>\-Typ oder den <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>\-Typ an den Attributkonstruktor.  
  
## Beispiel  
 Im folgenden Codebeispiel wird das Erstellen einer benutzerdefinierten Funktionsvalidierungsregel veranschaulicht:  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  