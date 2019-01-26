---
title: Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 248bf442924ab427b41875272771d2d55708f233
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870073"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Angaben Sie zu packen und-Bereitstellen in Projektelementen
  Alle SharePoint-Projektelemente in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügen über Eigenschaften, die Sie verwenden können, um zusätzliche Daten bereitstellen, wenn das Projekt in SharePoint bereitgestellt wird. Dort stehen die folgenden Eigenschaften zur Auswahl:  
  
- Featureeigenschaften  
  
- Feature-Empfänger  
  
- Projektausgabeverweise  
  
- Einträge für sicheres Steuerelement  
  
  Diese Eigenschaften werden der **Eigenschaften** Fenster.  
  
## <a name="feature-properties"></a>Funktionseigenschaften
 Verwenden der **Funktionseigenschaften** Eigenschaft, um Daten anzugeben, die die Funktion verwendet. Eigenschaften von Featuredaten ist einen Satz von Werten (gespeichert als Schlüssel/Wert-Paare), der mit einer Funktion enthalten ist, während der Bereitstellung in SharePoint. Nach dem Bereitstellen der Funktion können Sie im Code auf die Eigenschaftswerte zugreifen.  
  
 Wenn Sie einen Eigenschaftswert für die Funktion auf ein Projektelement hinzufügen, wird der Wert als ein Element in das Manifest der Funktion des Elements hinzugefügt. In einem Business Data Connectivity (BDC)-Modellprojekt z. B. featureeigenschaft ModelFileName wird als angezeigt:  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Nachdem Sie einen Feature-Eigenschaftswert festgelegt, wird es als FeatureProperty-Element des Projekts hinzugefügt *SPDATA* Datei. Informationen zum Zugreifen auf die Eigenschaften in SharePoint finden Sie unter [SPFeaturePropertyCollection-Klasse](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Identische Funktionseigenschaftswerte alle Projektelemente werden in das Funktionsmanifest zusammengeführt. Wenn zwei verschiedene Projektelemente den gleichen Schlüssel der Funktion mit nicht übereinstimmenden Werte angeben, tritt jedoch ein Überprüfungsfehler auf.  
  
 Funktionseigenschaften direkt an die Featuredatei hinzufügen (*.feature*), rufen Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Modell Objektmethode <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Wenn Sie diese Methode verwenden, achten Sie darauf, dass die gleiche Regel zum Hinzufügen von identischen Funktionseigenschaftswerte in Funktionseigenschaften auch, Eigenschaften, die direkt an die Featuredatei hinzugefügt gilt.  
  
## <a name="feature-receiver"></a>Funktionsempfänger
 Feature-Empfänger sind, dass Code, der ausgeführt wird, wenn bestimmte Ereignisse, auf ein Projektelement auftreten Funktion enthält. Beispielsweise können Sie Features Empfänger definieren, die ausgeführt werden, wenn das Feature installiert, aktiviert oder aktualisiert wird. Eine Möglichkeit zum Hinzufügen, ein Funktionsempfänger wird es direkt an eine Funktion hinzufügen, wie in beschrieben [Exemplarische Vorgehensweise: Hinzufügen von Funktionsereignisempfängern](../sharepoint/walkthrough-add-feature-event-receivers.md). Verweisen einen Namen der Empfängerklasse Feature und die Assembly in eine andere Möglichkeit ist die **Funktionsempfänger** Eigenschaft.  
  
### <a name="direct-method"></a>Direkte Methode
 Wenn Sie einen Funktionsempfänger direkt zu einer Funktion hinzufügen, wird eine Codedatei eingefügt, unter dem **Feature** Knoten im Projektmappen-Explorer. Wenn Sie die SharePoint-Lösung erstellen, wird der Code in eine Assembly kompiliert und in SharePoint bereitgestellt. Standardmäßig werden die Funktionseigenschaften **Empfängerassembly** und **Empfängerklasse** den Klassennamen und die Assembly zu verweisen.  
  
### <a name="reference-method"></a>Reference-Methode
 Eine weitere Möglichkeit, einen Funktionsempfänger hinzufügen, ist die Verwendung der **Funktionsempfänger** Eigenschaft eines Projektelements auf eine Funktionsempfängerassembly verweisen. Der Wert der Funktionsempfänger-Eigenschaft verfügt über zwei untergeordnete Eigenschaften: **Assembly** und **Klassenname**. Die Assembly muss der vollqualifizierte verwenden, muss "strong" und den Klassennamen der vollständige Typname sein. Weitere Informationen finden Sie unter [Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkID=169573). Nach dem Bereitstellen der lösungs in SharePoint, verwendet die Funktion den referenzierten Funktionsempfänger zum Behandeln von Ereignissen der Funktion.  
  
 Lösung Buildzeit, das Feature Werte der Empfänger auf die Funktion als auch die Projekte zum Festlegen von ReceiverAssembly und ReceiverClass Attribute der Feature-Elements in der SharePoint-Lösung Funktionsmanifest zusammengeführt (*WSP-Datei* ) Datei. Wenn die Assembly und Klassennamen an Eigenschaftswerte ein Projektelement und eine Funktion beide angegeben werden, müssen daher die Projekt-Element und die Funktion die Eigenschaftswerte übereinstimmen. Wenn die Werte nicht übereinstimmen, erhalten Sie einen Validierungsfehler. Wenn ein Projektelement eine Funktionsempfängerassembly als die verweisen verwendet die Funktion, verschieben Sie es auf ein weiteres Feature.  
  
 Wenn Sie eine Funktionsempfängerassembly, die auf dem Server noch nicht vorhanden ist verweisen, müssen Sie auch die Assemblydatei selbst in das Paket einschließen; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden nicht für Sie hinzugefügt. Wenn Sie die Funktion bereitstellen, wird die Assemblydatei kopiert, auf des Systems [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] oder den Ordner "Bin" im physischen Verzeichnis SharePoint. Weitere Informationen finden Sie unter Vorgehensweise: [Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Weitere Informationen zu Feature-Empfängern, finden Sie unter [Funktionsereignisempfänger](http://go.microsoft.com/fwlink/?LinkID=169574) und [Funktionsereignisse](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Projektausgabeverweise
 Die Eigenschaft Project Output References gibt es sich um eine Abhängigkeit, z. B. eine Assembly, auf das Projektelement ausführen. Nehmen wir beispielsweise an, dass Ihre Projektmappe ein BDC-Projekt und ein Projekt enthält. Verfügt das BDC-Projekt eine Abhängigkeit für die Assembly, die vom Klassenprojekt ausgegeben wird, können Sie die Assembly in Project Output References-Eigenschaft für das BDC-Projekt verweisen. Wenn das BDC-Projekt verpackt wird, wird die abhängige Assembly im Paket enthalten.  
  
 Projektausgabeverweise sind in der Regel Assemblys, aber in einigen Fällen (z. B. Silverlight-Projekte) andere Dateitypen werden können.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Projektausgabereferenz](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Einträge für sicheres Steuerelement
 SharePoint bietet einen Sicherheitsmechanismus, namens Einträge für sicheres Steuerelement, um den Zugriff von nicht vertrauenswürdigen Benutzern bestimmte Steuerelemente zu beschränken. Standardmäßig ermöglicht SharePoint nicht vertrauenswürdige Benutzer zum Hochladen und Erstellen von ASPX-Seiten auf dem SharePoint-Server. Um zu verhindern, dass diese Benutzer unsicheren Code ASPX-Seiten hinzufügen, schränkt SharePoint den Zugriff auf *sichere Steuerelemente*. Sichere Steuerelemente werden ASPX-Steuerelementen und Webparts, die als sicher gekennzeichnet, und, die von einem Benutzer auf Ihrer Website verwendet werden kann. Weitere Informationen finden Sie unter [Schritt 4: Hinzufügen des Webparts, die Liste der sicheren Steuerelemente](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Jede SharePoint-Projektelement in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügt über eine Eigenschaft namens **Einträge für sicheres Steuerelement** , zwei boolesche untergeordnete Eigenschaften besitzt: **Sichere** und **sicher vor Skripteinschleusung**. Die sichere Eigenschaft gibt an, ob nicht vertrauenswürdige Benutzer ein Steuerelement zugreifen können. Die sicher für Script-Eigenschaft gibt an, ob nicht vertrauenswürdige Benutzer anzeigen und Ändern der Eigenschaften eines Steuerelements können.  
  
 Einträge für sicheres Steuerelement werden auf Assemblybasis verwiesen. Sie Einträge für sicheres Steuerelement eines Projekts Assembly eingegeben werden, in des Projektelements hinzufügen **Einträge für sicheres Steuerelement** Eigenschaft. Sie können auch Einträge für sicheres Steuerelement hinzufügen, um der Assembly eines Projekts über die **erweitert** Registerkarte die **-Paket-Designer** Wenn Sie das Paket eine zusätzliche Assembly hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md) oder [Registrieren einer Web Part-Assembly als sicheres Steuerelement](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>XML-Einträge für sichere Steuerelemente
 Wenn Sie einen Eintrag für sicheres Steuerelement auf ein Projektelement oder der Assembly des Projekts hinzufügen, wird ein Verweis in das Paketmanifest im folgenden Format geschrieben:  
  
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
 [Paket und Bereitstellung von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Verwenden von Modulen zum Einfügen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
