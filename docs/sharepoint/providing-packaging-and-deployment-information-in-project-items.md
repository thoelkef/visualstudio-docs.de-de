---
title: "Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Funktionseigenschaften [SharePoint-Entwicklung in Visual Studio]"
  - "Funktionsempfänger [SharePoint-Entwicklung in Visual Studio]"
  - "Projektausgabeverweise [SharePoint-Entwicklung in Visual Studio]"
  - "Sichere Steuerelemente [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Erweiterte Tools zum Packen"
  - "SharePoint-Entwicklung in Visual Studio, Funktionseigenschaften"
  - "SharePoint-Entwicklung in Visual Studio, Funktionsempfänger"
  - "SharePoint-Entwicklung in Visual Studio, Projektausgabeverweise"
  - "SharePoint-Entwicklung in Visual Studio, Sichere Steuerelemente"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen
  Alle SharePoint\-Projektelemente in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügen über Eigenschaften, mit denen Sie weitere Daten angeben können, wenn das Projekt für SharePoint bereitgestellt wird.  Dort stehen die folgenden Eigenschaften zur Auswahl:  
  
-   Funktionseigenschaften  
  
-   Funktionsempfänger  
  
-   Projektausgabeverweise  
  
-   Einträge für sicheres Steuerelement  
  
 Diese Eigenschaften werden im Eigenschaftenfenster angezeigt.  
  
## Funktionseigenschaften  
 Die Eigenschaft **Funktionseigenschaften** dient zum Angeben von Daten, die von der Funktion verwendet werden.  Bei den Funktionseigenschaftendaten handelt es sich um einen Satz von Werten \(gespeichert als Schlüssel\-Wert\-Paare\), der beim Bereitstellen für SharePoint in eine Funktion eingeschlossen wird.  Nach dem Bereitstellen der Funktion können Sie im Code auf die Eigenschaftswerte zugreifen.  
  
 Wenn Sie einem Projektelement einen Funktionseigenschaftswert hinzufügen, wird dieser als Element in das Manifest der Funktion des Elements eingefügt.  So wird beispielsweise in einem Business Data Connectivity \(BDC\)\-Modellprojekt die ModelFileName\-Funktionseigenschaft folgendermaßen angezeigt:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Nach dem Festlegen eines Funktionseigenschaftswerts wird dieser der SPDATA\-Datei des Projekts als FeatureProperty\-Element hinzugefügt.  Informationen zum Zugreifen auf die Eigenschaften in SharePoint, Sie finden [SPFeaturePropertyCollections\-Klasse](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Identische Funktionseigenschaftswerte aus allen Projektelementen werden im Funktionsmanifest zusammengeführt.  Wenn jedoch zwei unterschiedliche Projektelemente den gleichen Funktionseigenschaftenschlüssel besitzen, die Werte aber nicht übereinstimmen, tritt ein Validierungsfehler auf.  
  
 Wenn Sie Funktionseigenschaften direkt der Funktionsdatei \(FEATURE\-Datei\) hinzufügen möchten, rufen Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint\-Objektmodellmethode "<xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>" auf.  Beachten Sie bei Verwendung dieser Methode, dass die Regel für das Hinzufügen von identischen Funktionseigenschaftswerten in Funktionseigenschaften auch für Eigenschaften gilt, die der Funktionsdatei direkt hinzugefügt werden.  
  
## Funktionsempfänger  
 Bei Funktionsempfängern handelt es sich um Code, der ausgeführt wird, wenn für die Funktion, in der ein Projektelement enthalten ist, bestimmte Ereignisse auftreten.  So können Sie beispielsweise Funktionsempfänger definieren, die ausgeführt werden, wenn die Funktion installiert, aktiviert oder aktualisiert wird.  Eine Möglichkeit zum Hinzufügen eines Funktionsempfängers besteht darin, ihn gemäß der Beschreibung unter [Exemplarische Vorgehensweise: Hinzufügen von Funktionsereignisempfängern](../sharepoint/walkthrough-add-feature-event-receivers.md) direkt einer Funktion hinzuzufügen.  Eine weitere Möglichkeit besteht im Erstellen eines Verweises auf den Klassennamen und die Assembly des Funktionsempfängers in der Eigenschaft **Funktionsempfänger**.  
  
### Direktmethode  
 Wenn Sie einer Funktion einen Funktionsempfänger direkt hinzufügen, wird im Projektmappen\-Explorer unter dem Knoten **Funktion** eine Codedatei eingefügt.  Beim Erstellen der SharePoint\-Lösung wird der Code in eine Assembly kompiliert und für SharePoint bereitgestellt.  Standardmäßig wird von den Funktionseigenschaften **Empfängerassembly** und **Empfängerklasse** auf den Klassennamen und die Assembly verwiesen.  
  
### Verweismethode  
 Ein Funktionsempfänger kann auch mithilfe der Eigenschaft **Funktionsempfänger** eines Projektelements hinzugefügt werden, indem mit der Eigenschaft auf eine Funktionsempfängerassembly verwiesen wird.  Der Eigenschaftswert für den Funktionsempfänger besitzt zwei untergeordnete Eigenschaften: **Assembly** und **Klassenname**.  Für die Assembly muss der vollqualifizierte, "starke" Name verwendet werden, und bei dem Klassennamen muss es sich um den vollständigen Typnamen handeln.  Weitere Informationen finden Sie unter [Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkID=169573).  Nach dem Bereitstellen der Lösung für SharePoint werden Funktionsereignisse mithilfe des referenzierten Funktionsempfängers gehandhabt.  
  
 Zur Erstellungszeit der Lösung werden die Eigenschaftswerte des Funktionsempfängers in der Funktion und in den Projekten zusammengeführt, um das ReceiverAssembly\-Attribut und das ReceiverClass\-Attribut des Feature\-Elements im Funktionsmanifest der SharePoint\-Lösungsdatei \(WSP\-Datei\) festzulegen.  Daher gilt Folgendes: Sind die Eigenschaftswerte sowohl für die Assembly als auch für den Klassennamen eines Projektelements und einer Funktion angegeben, müssen die Eigenschaftswerte von Projektelement und Funktion übereinstimmen.  Stimmen die Werte nicht überein, tritt ein Validierungsfehler auf.  Wenn von einem Projektelement auf eine Funktionsempfängerassembly verwiesen werden soll, die nicht der Assembly entspricht, die von der entsprechenden Funktion verwendet wird, verschieben Sie das Projektelement in eine andere Funktion.  
  
 Wenn Sie auf eine Funktionsempfängerassembly verweisen, die auf dem Server noch nicht vorhanden ist, muss auch die Assemblydatei selbst in das Paket eingeschlossen werden, da sie nicht automatisch von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hinzugefügt wird.  Durch Bereitstellen der Funktion wird die Assemblydatei entweder in den [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] des Systems oder in den Ordner "Bin" im physikalischen SharePoint\-Verzeichnis kopiert.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Weitere Informationen zu Funktionsempfängern finden, und [Funktions\-Ereignisse](http://go.microsoft.com/fwlink/?LinkID=169575) Sie [Funktionsereignisempfänger](http://go.microsoft.com/fwlink/?LinkID=169574).  
  
## Projektausgabeverweise  
 Mit der Eigenschaft "Projektausgabeverweise" wird eine Abhängigkeit \(beispielsweise eine Assembly\) angegeben, die zum Ausführen des Projektelements benötigt wird.  Nehmen Sie beispielsweise an, die Lösung verfügt über ein BDC\-Projekt und ein Klassenprojekt.  Wenn das BDC\-Projekt eine Abhängigkeit für die Assembly besitzt, die vom Klassenprojekt ausgegeben wird, können Sie in der Eigenschaft "Projektausgabeverweise" des BDC\-Projekts auf die Assembly verweisen.  Beim Packen des BDC\-Projekts wird die abhängige Assembly dem Paket hinzugefügt.  
  
 Projektausgabeverweise sind normalerweise Assemblys, in einigen Fällen kann es sich jedoch auch um andere Dateitypen handeln \(beispielsweise bei Silverlight\-Projekten\).  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer Projektausgabereferenz](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## Einträge für sicheres Steuerelement  
 Von SharePoint wird ein Sicherheitsmechanismus mit der Bezeichnung "Einträge für sicheres Steuerelement" bereitgestellt, um den Zugriff nicht vertrauenswürdiger Benutzer auf bestimmte Steuerelemente einzuschränken.  SharePoint ist so konzipiert, dass nicht vertrauenswürdigen Benutzern das Hochladen und Erstellen von ASPX\-Seiten auf dem SharePoint\-Server erlaubt wird.  Damit von diesen Benutzern kein unsicherer Code in ASPX\-Seiten eingefügt werden kann, wird der Zugriff dieser Benutzer auf *sichere Steuerelemente* beschränkt.  Sichere Steuerelemente sind als sicher geltende ASPX\-Steuerelemente und Webparts, die von jedem beliebigen Benutzer auf der Website verwendet werden können.  Weitere Informationen finden Sie unter [Schritt 4: Fügen Sie dem Webpart der Liste sicherer Steuerelemente hinzu](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Jedes SharePoint\-Projektelement in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügt über eine Eigenschaft, die **Einträge für sicheres Steuerelement**, die über zwei boolesche untergeordnete Eigenschaften verfügt: **Sicher** und **Sicher vor Skripteinschleusung**.  Die Eigenschaft "Sicher" gibt an, ob nicht vertrauenswürdige Benutzer auf ein Steuerelement zugreifen können.  Mit der Eigenschaft "Sicher vor Skripteinschleusung" wird angegeben, ob nicht vertrauenswürdige Benutzer die Eigenschaften eines Steuerelements anzeigen und ändern können.  
  
 Auf sichere Steuerelementeinträge wird auf Assemblybasis verwiesen.  Einträge für sichere Steuerelemente werden einem Projekt durch Eingeben in die Eigenschaft **Einträge für sicheres Steuerelement** des Projektelements hinzugefügt.  Einträge für sichere Steuerelemente können der Assembly eines Projekts jedoch auch über die Registerkarte **Erweitert** des Paket\-Designers hinzugefügt werden, wenn Sie dem Paket eine zusätzliche Assembly hinzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md) oder [Registrieren einer Webpart\-Assemblys als sicheres Steuerelement](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### XML\-Einträge für sichere Steuerelemente  
 Wenn Sie einem Projektelement oder der Assembly des Projekts einen Eintrag für sichere Steuerelemente hinzufügen, wird in das Paketmanifest ein Verweis im folgenden Format geschrieben:  
  
```  
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
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  