---
title: "Gewusst wie: Erstellen einer Masterseite oder eines Designs | Microsoft Docs"
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
  - "Importieren von Elementen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Importieren von Elementen"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Erstellen einer Masterseite oder eines Designs
  Sie können Seiten auf der SharePoint\-Website ein einheitliches Erscheinungsbild verleihen, indem Sie Masterseiten und Designs erstellen und verwenden.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stellt keine Vorlagen für diese Elemente, aber Sie können sie in SharePoint Designer erstellen und dann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importieren.  Weitere Informationen finden Sie auf [Baustein: Seiten und Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095) der Microsoft\-Website.  
  
### So importieren Sie eine Gestaltungsvorlage oder ein Design  
  
1.  Erstellen oder öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein SharePoint\-Projekt.  
  
     Weitere Informationen dazu, wie Sie ein SharePoint\-Projekt erstellen, finden Sie unter [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
3.  Erweitern Sie im Dialogfeld **Neues Element hinzufügen** den **SharePoint**\-Knoten und wählen Sie anschließend den Knoten **2010** aus.  
  
4.  In der Liste der SharePoint\-Vorlagen, wählen Sie die Vorlage **Modul** aus, und geben Sie einen Namen für das Modul an.  
  
     Ein Modul enthält Dateien \(beispielsweise, Masterseite oder Designdateien\) für Bereitstellung an einen Speicherort, den Sie in SharePoint angeben.  
  
5.  Löschen Sie im Modul die Standarddatei, die mit dem Namen Sample.txt.  
  
6.  Wählen Sie hierfür den Modulknoten aus.  
  
7.  Wählen Sie in der Menüleiste, **Vorhandenes Element hinzufügen**, **Projekt** und wählen Sie dann die Masterseite die oder Designdatei aus.  
  
     Gestaltungsvorlagendateien haben eine .master\-Erweiterung, und Designdateien haben eine .thmx\-Erweiterung.  
  
8.  Wenn Sie eine Gestaltungsvorlage hinzugefügt haben, ändern Sie die Einstellung **Bereitstellungskonfliktlösung** der **Automatisch** in den Eigenschaften des Moduls.  
  
    > [!NOTE]  
    >  Fehler können auftreten, wenn der Name der Gestaltungsvorlage der Gleiche ist wie der Name einer vorhandenen Gestaltungsvorlage, die entweder als Standardgestaltungsvorlage oder benutzerdefinierte Gestaltungsvorlage gekennzeichnet ist.  Informationen zum Beheben dieses Problems finden Sie unter [Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit Bild](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Im Modul öffnen Sie Elements.xml.  
  
     Sie müssen die Datei "Elements.xml" aktualisieren, um auf die Gestaltungsvorlage oder das Design zu verweisen, das Sie hinzugefügt haben.  
  
10. Ersetzen Sie für eine Gestaltungsvorlage das vorhandene Modulmarkup durch das folgende Markup:  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Ersetzen Sie für ein Design das vorhandene Modulmarkup durch das folgende Markup:  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Ersetzen Sie die Platzhalterwerte durch die tatsächlichen Namen des Moduls und der Gestaltungsvorlage oder des Designs.  
  
     Das `Type="GhostableInLibrary"`\-Attribut gibt an, dass der Inhaltsdatenbank das Element hinzugefügt wird, und das `Url`\-Attribut des Moduls gibt an, wo die Datei in der SharePoint\-Inhaltsdatenbank zu speichern ist.  
  
11. So Zum Ändern des Bereitstellungsbereichs für eine Gestaltungsvorlage, in **Projektmappen\-Explorer** zu ändern, öffnen die Funktionsdatei im Funktions\-Designer und wählen dann einen neuen Bereitstellungsbereich aus der Liste **Bereich** aus.  
  
     Ein Wert **Web** bedeutet, dass die Gestaltungsvorlage nur auf die Website angewendet wird, die gerade im Projekt angegeben ist.  Ein Wert **Site** bedeutet, dass die Gestaltungsvorlage für die aktuelle Websitesammlung gilt, die alle Unterwebsites und das Stammweb enthält.  Die anderen Werte sind nicht gültig.  
  
    > [!NOTE]  
    >  Da Designs nur für die Ebene der Websitesammlung gelten, empfiehlt es sich, den Bereich eines Designs ausschließlich auf **Site** festzulegen.  Fehler können auftreten, wenn ein Design in einer Unterwebsite verwendet wird.  
  
12. Wählen Sie in der Menüleiste **Projektmappe bereitstellen**, **Erstellen** aus.  
  
13. Um sicherzustellen dass die Dateien ordnungsgemäß bereitgestellt, die SharePoint\-Website geöffnet waren, das Menü **Websiteaktionen** auswählen, den Befehl **Websiteeinstellungen** auswählen und anschließend auf den Link **Masterseiten** oder den Link **Designs** wählen Sie.  
  
     Die Liste entweder von Masterseiten oder von Designs angezeigt und enthält entweder die Gestaltungsvorlage oder das Design, die Sie importiert haben.  
  
## Siehe auch  
 [Masterseiten](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Erstellen von Seiten für SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  