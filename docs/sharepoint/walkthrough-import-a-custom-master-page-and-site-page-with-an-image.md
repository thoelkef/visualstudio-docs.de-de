---
title: 'Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit einem Bild | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3fb68b4a84c6771c9430f2e8974ee485462b8563
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945844"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Exemplarische Vorgehensweise: Importieren Sie eine benutzerdefinierte Gestaltungsvorlage und einer Websiteseite mit einem Bild
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Importieren einer benutzerdefinierten SharePoint-Gestaltungsvorlage und einer Websiteseite mit Bild in einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt.  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie die folgenden Aufgaben ausgeführt werden:  
  
-   Erstellen Sie eine benutzerdefinierte Gestaltungsvorlage und eine Websiteseite unter Verwendung eines Images in SharePoint Designer.  
  
-   Exportieren Sie eine benutzerdefinierte Gestaltungsvorlage, Bild- und Seite "Website" in einer SharePoint-Lösung (*.wsp*) Datei.  
  
-   Importieren und Bereitstellen der *.wsp* Eingabedatei in eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt mit dem Import SharePoint Solution Package-Projekt.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Die folgenden Komponenten zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## <a name="create-items-in-sharepoint-designer"></a>Erstellen von Konfigurationselementen in SharePoint Designer
 Dieses Beispiel zeigt, wie Sie drei Elemente in SharePoint Designer für den Export zu erstellen: eine benutzerdefinierte Gestaltungsvorlage, eine Webseite, die die benutzerdefinierte Gestaltungsvorlage und einer Bilddatei auf der Seite "Website" angezeigt werden verweist. Das Bild wird in den Ordner "/ Images /" in SharePoint hinzugefügt.  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>So erstellen eine benutzerdefinierte Gestaltungsvorlage in SharePoint Designer
  
1.  Wählen Sie in SharePoint Designer, klicken Sie im Navigationsbereich die **Masterseiten** Site-Objekt.  
  
2.  Auf der **Masterseiten** im Menüband **leere Gestaltungsvorlage**.  
  
3.  Wählen Sie die neue Masterseite, und klicken Sie auf die **Masterseiten** im Menüband **Datei bearbeiten**.  
  
4.  Wählen Sie unten auf der SharePoint Designer, der **Code** Registerkarte.  
  
5.  Ersetzen Sie das vorhandene Markup durch das folgende Markup an.  
  
    ```aspx-csharp  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  Speichern Sie die Seite, wählen Sie die **Masterseiten** Registerkarte, und benennen Sie die Masterseite als **mybasic1.master**.  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Fügen Sie ein Bild in die Inhaltsdatenbank in SharePoint Designer
 Jetzt können Sie einem Bild zur Anzeige auf der Seite "Website" hinzufügen. Das Bild wird in der SharePoint-Inhaltsdatenbank bereitgestellt.  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Hinzufügen eines Bilds in die Inhaltsdatenbank in SharePoint Designer
  
1.  Wählen Sie im Navigationsbereich die **alle Dateien** site-Objekt, und wählen Sie in der Strukturansicht, dann die **Images** Ordner.  
  
2.  Auf der **alle Dateien** im Menüband **Importdateien**, wählen Sie eine Datei Ihrer Wahl, und wählen Sie dann die **OK** Schaltfläche. In diesem Beispiel die Datei heißt **myimg1.png**.  
  
     Optional können Sie einen Unterordner, um die Bilder organisieren erstellen.  
  
3.  Schließen der **Import** Dialogfeld.  
  
## <a name="create-a-site-page"></a>Erstellen Sie eine Standort-Seite
 Diese grundlegende-Seite verwendet die benutzerdefinierte Masterseite und zeigt das Bild, das Sie im vorherigen Schritt hinzugefügt haben.  
  
#### <a name="to-create-a-site-page"></a>Zum Erstellen einer Site-Seite  
  
1.  Wählen Sie im Navigationsbereich die **Websiteseiten** Objekt.  
  
2.  Auf der **Seiten** im Menüband der **Seite** Schaltfläche der **ASPX** Seite Art, und nennen Sie die neue Datei **mycontentpage1.aspx**.  
  
     Optional können Sie einen Unterordner zum Organisieren von Websiteseiten erstellen.  
  
3.  Wählen Sie in der Liste Website Seiten **MyContentPage1.aspx** , öffnen Sie die Seite "Eigenschaften", und wählen Sie dann am unteren Rand der Seite, die **bearbeiten Datei** Link.  
  
     Wenn eine Meldung angezeigt wird und besagt, dass diese Seite keine Regionen enthält, die im abgesicherten Modus bearbeitet werden und fragt, ob Sie verwenden möchten, öffnen auf dieser Seite im erweiterten Modus, und wählen die **Ja** Schaltfläche.  
  
4.  Wählen Sie am unteren Rand der Seite, die **Code** Schaltfläche.  
  
5.  Ersetzen Sie das vorhandene Markup durch das folgende Markup an.  
  
    ```aspx-csharp  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  Speichern Sie die Seite für die aktualisierten Standorts.  
  
## <a name="export-the-items-from-sharepoint"></a>Exportieren Sie die Elemente aus SharePoint
 Exportieren Sie die Elemente aus SharePoint in einer SharePoint-Lösung (*.wsp*) Datei.  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>Exportieren von Elementen aus SharePoint Designer
  
1.  Wählen Sie in SharePoint Designer, klicken Sie im Navigationsbereich die **Teamwebsite** -Objekt, und klicken Sie auf die **Standort** im Menüband **als Vorlage speichern**.  
  
2.  In der **als Vorlage speichern** Dialogfeld Geben Sie einen Dateinamen und den Vorlagennamen ein, wählen die **Inhalte einschließen** aus, und wählen Sie dann die **OK** Schaltfläche.  
  
     Dies speichert den Inhalt des Standorts in der *.wsp* Datei.  
  
3.  Wählen Sie nach die Lösung exportiert, die **Lösungskatalog** Link, um die Liste der verfügbaren Lösungsdateien anzuzeigen.  
  
4.  Öffnen Sie das Kontextmenü für das neue *.wsp* Datei, und wählen Sie dann **Ziel speichern unter** auf das System zu speichern.  
  
## <a name="import-the-items-into-visual-studio"></a>Importieren Sie die Elemente in Visual Studio
 Importieren der *.wsp* in Datei [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Nach dem Importieren des Inhalts können Sie anpassen, weitere Elemente hinzufügen und anschließend bereitstellen.  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Importieren von Elementen aus der WSP-Datei in Visual Studio  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie eine **SharePoint 2010-Lösungspaket importieren** Projekt.  
  
2.  Auf der **zu importierende Elemente auswählen** Seite **Modul** in die **Typ** Spalte, die Kontrollkästchen für die nur die Dateien in der folgenden Tabelle für den Import.  
  
    |Dateiname|Beschreibung|  
    |---------------|-----------------|  
    |\_catalogsmasterpage\_|Die benutzerdefinierte Masterseite.|  
    |images_|Die Bilddatei im SharePoint-Dateisystem.|  
    |SitePages_|Die Websiteseite.|  
  
3.  Wählen Sie die **Fertig stellen** Schaltfläche, um die ausgewählten Elemente zu importieren.  
  
4.  In **Projektmappen-Explorer**, wählen Sie die \_Catalogsmasterpage\_ Knoten, und legen Sie den Wert der seine **Bereitstellungskonfliktlösung** Eigenschaft **automatische** .  
  
     Dadurch wird sichergestellt, dass alle Bereitstellungskonflikte automatisch aufgelöst werden.  
  
5.  Weist die neue Masterseite auf den gleichen Namen wie eine vorhandene Seite, stellen Sie sicher, dass die vorhandene Seite als eine Standard-Masterseite oder einer benutzerdefinierten Gestaltungsvorlage in SharePoint Designer nicht gekennzeichnet ist.  
  
     Wenn eine master-Seite als Standardgestaltungsvorlage oder benutzerdefinierten Gestaltungsvorlage markiert ist, erhalten Sie einen Fehler bei der Bereitstellung, der besagt, dass die Masterseite kann nicht gelöscht werden. Zur Vermeidung dieses Problems folgende Schritte:  
  
    -   Wenn die vorhandene Masterseite als Standardgestaltungsvorlage festgelegt ist, müssen Sie vorübergehend eine andere Masterseite als Standardgestaltungsvorlage festgelegt. Nachdem Sie die Dateien in SharePoint bereitstellen, legen Sie die neue Masterseite als Standardgestaltungsvorlage.  
  
    -   Wenn die vorhandene Masterseite als benutzerdefinierte Gestaltungsvorlage festgelegt ist, müssen Sie vorübergehend einen anderen Masterseite als benutzerdefinierte Gestaltungsvorlage festgelegt. Nachdem Sie die Dateien in SharePoint bereitstellen, legen Sie die neue Masterseite als benutzerdefinierte Gestaltungsvorlage.  
  
6.  Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe bereitstellen**.  
  
7.  Öffnen Sie die SharePoint-Website, um die bereitgestellten Elemente anzuzeigen.  
  
 Eine alternative Möglichkeit zum Importieren von Dateien in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sowie bereitstellen auf SharePoint ist das Hinzufügen von Dateien in den Modulen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Gewusst wie: Importieren einer Masterseite oder eines Designs](../sharepoint/how-to-import-a-master-page-or-theme.md) und [Verwenden von Modulen zum Einfügen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Siehe auch
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
