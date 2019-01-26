---
title: 'Vorgehensweise: Importieren einer Masterseite oder eines Designs | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: af0f7ad40c1e06f1c602f17ba6a80cf47b96ed0e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863369"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Vorgehensweise: Importieren einer Masterseite oder eines Designs
  Sie können Seiten auf Ihrer SharePoint-Website ein einheitliches Erscheinungsbild verleihen durch Erstellen und Verwenden von Masterseiten und Designs. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nicht für diese Elemente stellen Vorlagen bereit, aber Sie können sie in SharePoint Designer erstellen und importieren Sie sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Baustein: Seiten und Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095) auf der Microsoft-Website.  
  
### <a name="to-import-a-master-page-or-theme"></a>Zum Importieren einer Masterseite oder eines Designs  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]erstellen oder öffnen Sie ein SharePoint-Projekt.  
  
     Weitere Informationen zum Erstellen eines SharePoint-Projekts, finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.  
  
3.  In der **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der SharePoint-Vorlagen, die **Modul** Vorlage, und klicken Sie dann einen Namen für das Modul angeben.  
  
     Ein Modul enthält Dateien (z. B. "Masterseite" oder "Dateien") für die Bereitstellung an einem Speicherort, den Sie in SharePoint angeben.  
  
5.  Löschen Sie die Standard-Datei, mit dem Namen des Moduls *"Sample.txt"*.  
  
6.  Wählen Sie den Knoten "Module" aus.  
  
7.  Wählen Sie auf der Menüleiste **Projekt** > **vorhandenes Element hinzufügen**, und wählen Sie dann auf die Seite oder eines Designs Masterdatei.  
  
     Masterseitendateien haben eine Master-Erweiterung und Designdateien haben die Erweiterung thmx.  
  
8.  Wenn Sie eine Masterseite hinzugefügt haben, ändern die **Bereitstellungskonfliktlösung** auf **automatische** in die Eigenschaften des Moduls.  
  
    > [!NOTE]  
    >  Fehler können auftreten, wenn der Name der Masterseite ist identisch mit den Namen einer vorhandenen master-Seite, die als Standardgestaltungsvorlage oder benutzerdefinierten Gestaltungsvorlage markiert ist. Informationen zum Beheben dieses Problems finden Sie unter [Exemplarische Vorgehensweise: Importieren Sie eine benutzerdefinierte Gestaltungsvorlage und einer Websiteseite mit einem Bild](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Öffnen Sie im Modul *"Elements.xml"*.  
  
     Müssen Sie aktualisieren die *"Elements.xml"* Datei auf der Masterseite oder Design, das Sie hinzugefügt haben.  
  
10. Ersetzen Sie für eine Masterseite das vorhandene Modulmarkup durch das folgende Markup.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Ersetzen Sie ein Design das vorhandene Modulmarkup durch das folgende Markup.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Achten Sie darauf, dass Sie die Platzhalterwerte durch die tatsächlichen Namen des Moduls und die Masterseite oder Design zu ersetzen.  
  
     Das Attribut `Type="GhostableInLibrary"` gibt an, dass das Element in der Inhaltsdatenbank hinzugefügt wird und die `Url` Attribut des Moduls wird angegeben, wo die Datei in der SharePoint-Inhaltsdatenbank gespeichert.  
  
11. So ändern Sie den Bereitstellungsumfang für eine Masterseite in **Projektmappen-Explorer**, öffnen Sie die Featuredatei in der Funktions-Designer, und wählen Sie dann einen neuen Bereich der Bereitstellung aus dem **Bereich** Liste.  
  
     Der Wert **Web** bedeutet, die die Masterseite nur für die Website angewendet werden, die derzeit im Projekt angegeben ist. Der Wert **Site** bedeutet, dass die Masterseite auf der aktuellen Websitesammlung anwendet, umfasst alle Unterwebsites und das Stamm-Web. Die anderen Werte gelten nicht.  
  
    > [!NOTE]  
    >  Da nur auf Ebene der Websitesammlung Designs angewendet werden, es wird empfohlen, dass Sie nicht im Rahmen eines Designs auf irgendetwas außer festlegen **Site**. Fehler können auftreten, wenn ein Design in einem untergeordneten Standort verwendet wird.  
  
12. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe bereitstellen**.  
  
13. Um zu überprüfen, ob die Dateien richtig bereitgestellt wurden, öffnen Sie die SharePoint-Website, wählen Sie die **Websiteaktionen** im Menü Wählen Sie die **Standorteinstellungen** Befehl aus, und wählen Sie dann entweder die **Masterseiten**  Link oder **Designs** Link.  
  
     Die Liste von Masterseiten oder Designs wird angezeigt und enthält die Masterseite oder das Design, das Sie importiert haben.  
  
## <a name="see-also"></a>Siehe auch
 [Masterseiten](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Erstellen von Seiten für SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Verwenden von Modulen zum Einfügen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
