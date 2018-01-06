---
title: "Vorgehensweise: Erstellen von benutzerdefinierten Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen | Microsoft Docs"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 20a56a2f6582a08270292cd86cf62a9344d8565f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Gewusst wie: Erstellen von benutzerdefinierten Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen
  Sie können benutzerdefinierte Validierungsregeln, um zu überprüfen, das Lösungspaket, generiert Visual Studio erstellen. Sie können eine gesamte Funktion oder ein Paket vollständige Überprüfung ausführen, indem Sie auswählen **Validate** aus dem Kontextmenü für ein Paket oder eine Funktion in der **PackagingExplorer**. Teilweisen Validierung wird ausgeführt, wenn Sie neue SharePonit Projektelemente oder Funktionen, das Projekt hinzufügen, um zu bestimmen, ob das Paket oder eine Funktion in einem gültigen Zustand wäre.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Um eine benutzerdefinierte Paketvalidierungsregel zu erstellen.  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die eine der folgenden Schnittstellen implementiert:  
  
    -   Um eine Paketvalidierungsregel zu erstellen, implementieren die <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> Schnittstelle.  
  
    -   Um eine Funktionsvalidierungsregel zu erstellen, implementieren die <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> Schnittstelle.  
  
4.  Hinzufügen der <xref:System.ComponentModel.Composition.ExportAttribute> auf die Klasse. Dieses Attribut ermöglicht Visual Studio ermitteln und laden die Validierungsregel. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> oder <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> Typ an den Attributkonstruktor.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine benutzerdefinierte Funktionsvalidierungsregel zu erstellen.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition hinzu.  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Packen und -Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  