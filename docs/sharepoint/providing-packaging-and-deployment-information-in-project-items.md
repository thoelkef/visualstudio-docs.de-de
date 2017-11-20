---
title: Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5f12b3af8f49270cc914e47a37077265794bf0be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen
  Alle SharePoint-Projektelemente im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügen über Eigenschaften, die Sie verwenden können, um zusätzliche Daten bereitzustellen, wenn das Projekt für SharePoint bereitgestellt wird. Dort stehen die folgenden Eigenschaften zur Auswahl:  
  
-   Funktionseigenschaften  
  
-   Feature-Empfänger  
  
-   Projektausgabeverweise  
  
-   Einträge für sicheres Steuerelement  
  
 Diese Eigenschaften werden der **Eigenschaften** Fenster.  
  
## <a name="feature-properties"></a>Featureeigenschaften  
 Verwenden der **Funktionseigenschaften** Eigenschaft, um Daten anzugeben, die die Funktion verwendet. Eigenschaften der Funktionsdaten ist ein Satz von Werten (gespeichert als Schlüssel/Wert-Paare), der beim Bereitstellen für SharePoint in eine Funktion eingeschlossen wird. Nach dem Bereitstellen der Funktion können Sie im Code auf die Eigenschaftswerte zugreifen.  
  
 Wenn Sie ein Projektelement Wert einer Funktion hinzufügen, wird der Wert als ein Element in das Manifest der Funktion für das Element hinzugefügt. In einem Business Data Connectivity (BDC) Modellprojekt z. B. die ModelFileName Funktionseigenschaft folgendermaßen angezeigt:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Nachdem Sie einen Feature-Eigenschaftswert festgelegt, wird er als FeatureProperty-Element in der Projektdatei SPDATA hinzugefügt. Informationen zum Zugreifen auf die Eigenschaften in SharePoint finden Sie unter [SPFeaturePropertyCollection Klasse](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Identische Funktionseigenschaftswerte aus allen Projektelementen werden im Funktionsmanifest zusammengeführt. Wenn zwei verschiedene Projektelemente den gleichen Schlüssel der Funktion mit nicht übereinstimmenden Werten angeben, tritt jedoch ein Validierungsfehler auf.  
  
 Hinzuzufügende Funktionseigenschaften direkt an die Featuredatei (* .feature), rufen Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Object Model-Methode <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Wenn Sie diese Methode verwenden, Bedenken Sie, dass die gleiche Regel zum Hinzufügen von Identische Funktionseigenschaftswerte in Funktionseigenschaften auch für Eigenschaften, die direkt an die Featuredatei hinzugefügt gilt.  
  
## <a name="feature-receiver"></a>Funktionsempfänger  
 Feature Empfänger sind, dass Code, der ausgeführt wird, wenn bestimmte Ereignisse, in der ein Projektelement eintreten Funktion enthält. Sie können z. B. Feature Empfänger definieren, die ausgeführt werden, wenn das Feature installiert, aktiviert oder aktualisiert wird. Eine Möglichkeit zum Hinzufügen, ein Funktionsempfänger besteht darin, sie direkt an eine Funktion hinzuzufügen, wie in beschrieben [Exemplarische Vorgehensweise: Hinzufügen von Funktionsereignisempfängern](../sharepoint/walkthrough-add-feature-event-receivers.md). Eine andere Möglichkeit ist, verweisen auf ein Funktionsname Empfänger-Klasse und die Assembly in die **Funktionsempfänger** Eigenschaft.  
  
### <a name="direct-method"></a>Direkte Methode  
 Wenn Sie einen Funktionsempfänger direkt an eine Funktion hinzufügen, wird eine Codedatei unter platziert die **Feature** Knoten im Projektmappen-Explorer. Wenn Sie die SharePoint-Lösung erstellen, wird der Code in eine Assembly kompiliert und auf SharePoint bereitgestellt. Standardmäßig wird die Funktionseigenschaften **Empfängerassembly** und **Empfängerklasse** verweisen auf die Klassennamen und die Assembly.  
  
### <a name="reference-method"></a>Reference-Methode  
 Eine andere Möglichkeit, einen Funktionsempfänger hinzufügen, ist die Verwendung der **Funktionsempfänger** Eigenschaft, der ein Projektelement zum Verweisen auf eine Funktion Empfänger-Assembly. Der Eigenschaftswert Funktionsempfänger besitzt zwei untergeordnete Eigenschaften: **Assembly** und **Klassenname**. Die Assembly muss der vollqualifizierte verwenden, "strong" Name und der Klassenname muss der vollständige Typname sein. Weitere Informationen finden Sie unter [Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkID=169573). Nach der Bereitstellung der Projektmappe in SharePoint verwendet die Funktion dem referenzierten Funktionsempfänger Feature Ereignisse behandeln.  
  
 Zur Buildzeit Lösung zusammenführen die Feature-Empfänger-Eigenschaftswerte in der Funktions- und deren Projekte die ReceiverAssembly und ReceiverClass Attribute des Elements Feature in dem Funktionsmanifest der SharePoint-Lösungsdatei (WSP) festlegen. Wenn die Assembly und Klassennamen Eigenschaftswerte eines Projektelements und eine Funktion beide angegeben werden, müssen daher Eigenschaftswerte für das Projekt Element und Funktion übereinstimmen. Wenn die Werte nicht übereinstimmen, erhalten Sie einen Validierungsfehler. Gegebenenfalls ein Projektelement verweisen eine Funktion Empfängerassembly als die in der Funktion verwendet wird, verschieben Sie sie an eine andere Funktion.  
  
 Wenn Sie eine Funktion Empfängerassembly, die nicht bereits auf dem Server befindet verweisen, müssen Sie auch die Assemblydatei selbst in das Paket einschließen; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden nicht für Sie hinzugefügt. Wenn Sie die Funktion bereitstellen, wird die Assemblydatei kopiert, auf des Systems [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] oder der Ordner "Bin" im physischen Verzeichnis SharePoint. Weitere Informationen finden Sie unter Vorgehensweise: [wie: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Weitere Informationen zum Feature Empfänger finden Sie unter [Funktionsereignisempfängers](http://go.microsoft.com/fwlink/?LinkID=169574) und [Funktionsereignisse](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Projektausgabeverweise  
 Die Projektausgabeverweise-Eigenschaft gibt eine Abhängigkeit, z. B. eine Assembly, die zum Ausführen des Projektelements benötigt. Nehmen Sie beispielsweise an, dass Ihre Lösung ein BDC-Projekt und einem Projekt verwendet. Wenn das BDC-Projekt eine Abhängigkeit für die Assembly, die vom Klassenprojekt ausgegeben wird verfügt, können Sie die Assembly in das BDC-Projekt Projektausgabeverweise Eigenschaft verweisen. Wenn das BDC-Projekt verpackt wird, wird die abhängige Assembly im Paket enthalten.  
  
 Projektausgabeverweise sind normalerweise Assemblys, aber in einigen Fällen (z. B. Silverlight-Projekte) andere Dateitypen werden können.  
  
 Weitere Informationen finden Sie unter [wie: Hinzufügen einer Projektausgabereferenz](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Einträge für sicheres Steuerelement  
 SharePoint bietet einen Sicherheitsmechanismus namens Einträge für sicheres Steuerelement, um den Zugriff auf bestimmte Steuerelemente nicht vertrauenswürdige Benutzer einzuschränken. Programmbedingt ermöglicht SharePoint nicht vertrauenswürdige Benutzer hochladen und ASPX-Seiten auf dem SharePoint-Server erstellen. Um zu verhindern, dass diese Benutzer ASPX-Seiten unsicheren Code hinzugefügt, SharePoint schränkt den Zugriff auf *sichere Steuerelemente*. Sichere Steuerelemente werden ASPX-Steuerelemente und Webparts, die als sicher gekennzeichnet, und, die von einem Benutzer auf Ihrer Website verwendet werden kann. Weitere Informationen finden Sie unter [Schritt 4: Hinzufügen des Webparts in der Sicherungsliste Steuerelemente](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Jede SharePoint-Projektelement in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält eine Eigenschaft namens **Einträge für sicheres Steuerelement** , besitzt zwei boolesche Untereigenschaften: **sichere** und **sicher für Skript**. Die sichere Eigenschaft gibt an, ob nicht vertrauenswürdige Benutzer auf ein Steuerelement zugreifen können. Die sichere für Script-Eigenschaft gibt an, ob nicht vertrauenswürdige Benutzer können anzeigen und Ändern von Eigenschaften des Steuerelements.  
  
 Einträge für sicheres Steuerelement regelmäßig eine Assembly verwiesen wird. Sie Assembly des Projekts Einträge für sicheres Steuerelement hinzufügen, indem Sie sie in des Projektelements eingeben **Einträge für sicheres Steuerelement** Eigenschaft. Sie können auch Einträge für sicheres Steuerelement hinzufügen, um eine Projektassembly über die **erweitert** Registerkarte der **Paket-Designer** beim Hinzufügen einer weiteren Assembly für das Paket. Weitere Informationen finden Sie unter [wie: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md) oder [Registrieren einer Web-Teilassembly als ein sicheres Steuerelement](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>XML-Einträge für sichere Steuerelemente  
 Wenn Sie einen sicheres Steuerelement-Eintrag in der ein Projektelement oder der Assembly des Projekts hinzufügen, wird ein Verweis in Paketmanifest im folgenden Format geschrieben:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Erweitern von SharePoint-Packen und -Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  