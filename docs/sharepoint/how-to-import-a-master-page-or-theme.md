---
title: 'Vorgehensweise: Importieren einer Masterseite oder Design | Microsoft Docs'
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 07c3e9fb88ea562a85e1c7555d2c57cb04d769ff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-import-a-master-page-or-theme"></a>Gewusst wie: Erstellen einer Masterseite oder eines Designs
  Sie können Seiten auf der SharePoint-Website ein einheitliches Erscheinungsbild verleihen durch Erstellen und Verwenden von Masterseiten und Designs. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]nicht für diese Elemente stellen Vorlagen bereit, aber Sie können sie in SharePoint Designer erstellen und dann importieren Sie sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Baustein: Seiten und Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095) auf der Microsoft-Website.  
  
### <a name="to-import-a-master-page-or-theme"></a>So importieren Sie eine Gestaltungsvorlage oder Design  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]erstellen oder öffnen Sie ein SharePoint-Projekt.  
  
     Informationen zum Erstellen eines SharePoint-Projekts finden Sie unter [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der SharePoint-Vorlagen, die **Modul** Vorlage, und geben Sie einen Namen für das Modul.  
  
     Ein Modul enthält Dateien (z. B. Gestaltungsvorlage oder Designdateien) für die Bereitstellung an einem Speicherort, den Sie in SharePoint angeben.  
  
5.  Löschen Sie die standardmäßige Datei mit die Namen "Sample.txt" im Modul.  
  
6.  Wählen Sie den Modul aus.  
  
7.  Wählen Sie in der Menüleiste **Projekt**, **vorhandenes Element hinzufügen**, und wählen Sie dann die Masterdatei Seiten- oder Design.  
  
     Master Auslagerungsdateien .master Erweiterung aufweisen, und Designdateien haben die Erweiterung thmx.  
  
8.  Ändern, wenn Sie eine Masterseite hinzugefügt, dessen **Bereitstellungskonfliktlösung** auf **automatische** in die Eigenschaften des Moduls.  
  
    > [!NOTE]  
    >  Fehler können auftreten, wenn der Name der Masterseite ist identisch mit den Namen einer vorhandenen master-Seite, die als Standardgestaltungsvorlage oder benutzerdefinierte Gestaltungsvorlage gekennzeichnet ist. Informationen zum Lösen dieses Problems finden Sie unter [Exemplarische Vorgehensweise: Importieren Sie eine benutzerdefinierte Gestaltungsvorlage und einer Websiteseite mit einem Bild](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Öffnen Sie im Modul "Elements.xml".  
  
     Aktualisieren Sie die Datei "Elements.xml" verweisen, der Gestaltungsvorlage oder das Design, das Sie hinzugefügt haben.  
  
10. Ersetzen Sie das vorhandene Modulmarkup für eine Gestaltungsvorlage durch Folgendes Markup.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Ersetzen Sie das vorhandene Modulmarkup für ein Design durch Folgendes Markup.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Achten Sie darauf, dass die Platzhalterwerte durch die tatsächlichen Namen des Moduls und der Gestaltungsvorlage oder Design zu ersetzen.  
  
     Das Attribut `Type="GhostableInLibrary"` gibt an, dass das Element in der Inhaltsdatenbank hinzugefügt wird und die `Url` Attribut des Moduls gibt an, wo die Datei in der SharePoint-Inhaltsdatenbank gespeichert.  
  
11. So ändern Sie den Bereich der Bereitstellung einer Masterseite in **Projektmappen-Explorer**, öffnen Sie die Featuredatei, in dem Funktions-Designer, und wählen Sie dann einen neue Bereitstellung Bereich aus der **Bereich** Liste.  
  
     Der Wert **Web** bedeutet, die die Gestaltungsvorlage nur für die Website gilt, die derzeit im Projekt angegeben ist. Der Wert **Website** bedeutet, dass die Gestaltungsvorlage der aktuellen Websitesammlung gilt gehören alle Standorte und der Stammwebsite. Die anderen Werte sind nicht anwendbar.  
  
    > [!NOTE]  
    >  Da Designs nur auf der Ebene der Websitesammlung anwenden möchten, empfiehlt es sich, dass Sie nicht den Bereich eines Designs zu beliebiegen Dokumentbestandteilen außer festlegen **Website**. Fehler können auftreten, wenn ein Design in einer Unterwebsite verwendet wird.  
  
12. Wählen Sie in der Menüleiste **erstellen**, **Projektmappe bereitstellen**.  
  
13. Um zu überprüfen, ob die Dateien ordnungsgemäß bereitgestellt wurden, öffnen Sie die SharePoint-Website, wählen Sie die **Websiteaktionen** Menü Wählen Sie die **Standorteinstellungen** Befehl, und wählen Sie dann entweder die **Masterseiten**  Link oder **Designs** Link.  
  
     Die Liste der Gestaltungsvorlagen oder Designs wird angezeigt und enthält die Gestaltungsvorlage oder das Design, das Sie importiert haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Masterseiten](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Erstellen von Seiten für SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  