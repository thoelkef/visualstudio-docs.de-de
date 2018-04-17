---
title: 'Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit einem Bild | Microsoft Docs'
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
ms.openlocfilehash: f90f85e7f22cf3bdecf90aaf6f8d61af3f399a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit Bild
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine benutzerdefinierte SharePoint-Gestaltungsvorlage und eine Websiteseite mit einem Bild Importieren einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt.  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie die folgenden Aufgaben ausgeführt werden:  
  
-   Erstellen Sie eine benutzerdefinierte Gestaltungsvorlage und eine Websiteseite unter Verwendung eines Images im SharePoint-Designer an.  
  
-   Exportieren Sie eine benutzerdefinierte Gestaltungsvorlage, Bild und Websiteseite in eine SharePoint-Lösungsdatei (WSP).  
  
-   Importieren und Bereitstellen die WSP-Datei in eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt mit dem SharePoint-Lösungspaket importieren-Projekt.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Die folgenden Komponenten zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## <a name="create-items-in-sharepoint-designer"></a>Erstellen von Elementen im SharePoint-Designer  
 In diesem Beispiel wird gezeigt, wie drei Elemente in SharePoint Designer für den Export zu erstellen: eine benutzerdefinierte Gestaltungsvorlage, eine Websiteseite, die verweist auf die benutzerdefinierte Gestaltungsvorlage und einer Bilddatei auf der Seite angezeigt werden. Das Bild wird in den Ordner "/ Images /" in SharePoint hinzugefügt.  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>So erstellen Sie eine benutzerdefinierte Gestaltungsvorlage in SharePoint Designer  
  
1.  Wählen Sie im SharePoint-Designer, klicken Sie im Navigationsbereich die **Masterseiten** Standortobjekt.  
  
2.  Auf der **Masterseiten** Menüband **leere Gestaltungsvorlage**.  
  
3.  Wählen Sie die neue Masterseite, und klicken Sie auf die **Masterseiten** Menüband **Datei bearbeiten**.  
  
4.  Klicken Sie unten auf der SharePoint-Designer wählen Sie die **Code** Registerkarte.  
  
5.  Ersetzen Sie das vorhandene Markup durch das folgende Markup.  
  
    ```  
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
  
6.  Speichern Sie die Seite, wählen Sie die **Masterseiten** Registerkarte, und benennen Sie die Gestaltungsvorlage als **mybasic1.master**.  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Hinzufügen eines Bilds in der Inhaltsdatenbank im SharePoint-Designer  
 Jetzt können Sie einem Bild zur Anzeige auf der Seite hinzufügen. Das Bild wird in der SharePoint-Inhaltsdatenbank bereitgestellt.  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Zum Hinzufügen eines Bilds in der Inhaltsdatenbank im SharePoint-Designer  
  
1.  Wählen Sie im Navigationsbereich die **alle Dateien** site-Objekt, und wählen Sie dann in der Strukturansicht der **Bilder** Ordner.  
  
2.  Auf der **alle Dateien** Menüband **Dateien importieren**, wählen Sie eine Datei Ihrer Wahl ein, und wählen Sie dann die **OK** Schaltfläche. In diesem Beispiel wird die Datei heißt **myimg1.png**.  
  
     Optional können Sie einen Unterordner zum Organisieren von Images erstellen.  
  
3.  Schließen der **Import** (Dialogfeld).  
  
## <a name="create-a-site-page"></a>Erstellen Sie eine Websiteseite  
 Diese grundlegenden Websiteseite verwendet die benutzerdefinierte Gestaltungsvorlage und zeigt das Bild, das Sie im vorherigen Schritt hinzugefügt.  
  
#### <a name="to-create-a-site-page"></a>So erstellen eine Websiteseite  
  
1.  Wählen Sie im Navigationsbereich die **Websiteseiten** Objekt.  
  
2.  Auf der **Seiten** Menüband der **Seite** Schaltfläche der **ASPX** Seite ", und benennen Sie die neue Datei **mycontentpage1.aspx**.  
  
     Optional können Sie einen Unterordner zum Organisieren von den Seiten der Website erstellen.  
  
3.  Wählen Sie in der Liste Website Seiten **MyContentPage1.aspx** , öffnen Sie die Seite "Eigenschaften", und wählen Sie dann am unteren Rand der Seite, die **bearbeiten Datei** Link.  
  
     Wenn eine Meldung angezeigt wird und besagt, dass diese Seite keine Bereiche enthalten, die im abgesicherten Modus bearbeitet werden und fragt, ob Sie verwenden möchten, öffnen Sie die Seite im erweiterten Modus, wählen die **Ja** Schaltfläche.  
  
4.  Wählen Sie am unteren Rand der Seite, die **Code** Schaltfläche.  
  
5.  Ersetzen Sie das vorhandene Markup durch das folgende Markup.  
  
    ```  
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
  
6.  Speichern Sie die aktualisierte Websiteseite.  
  
## <a name="export-the-items-from-sharepoint"></a>Exportieren Sie die Elemente aus SharePoint  
 Die Elemente aus SharePoint in eine SharePoint-Lösungsdatei (WSP-Datei) exportieren.  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>So exportieren Sie Elemente aus dem SharePoint-Designer  
  
1.  Wählen Sie im SharePoint-Designer, klicken Sie im Navigationsbereich die **Teamwebsite** -Objekt, und klicken Sie auf die **Website** Menüband **als Vorlage speichern**.  
  
2.  In der **als Vorlage speichern** Dialogfeld Geben Sie einen Dateinamen und den Vorlagennamen, wählen die **Inhalte** Kontrollkästchen, und wählen Sie dann die **OK** Schaltfläche.  
  
     Dies speichert den Inhalt des Standorts an, in der WSP-Datei.  
  
3.  Nachdem die Projektmappe exportiert werden soll, wählen Sie die **Solution Gallery** Link, um die Liste der verfügbaren Projektmappendateien anzuzeigen.  
  
4.  Öffnen Sie das Kontextmenü für die neue WSP-Datei, und wählen Sie dann **Ziel speichern unter** auf dem System zu speichern.  
  
## <a name="import-the-items-into-visual-studio"></a>Importieren Sie die Elemente in Visual Studio  
 Importieren Sie die WSP-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Nach dem Importieren des Inhalts können Sie anpassen, weitere Elemente hinzufügen und dann bereitstellen.  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Importieren von Elementen aus der WSP-Datei in Visual Studio  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie eine **SharePoint 2010-Lösungspaket importieren** Projekt.  
  
2.  Auf der **Elemente auswählen, um importieren** Seite **Modul** in der **Typ** Spalte, die Kontrollkästchen für die nur die Dateien in der folgenden Tabelle für den Import.  
  
    |Dateiname|Beschreibung|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|Die benutzerdefinierte Gestaltungsvorlage.|  
    |images_|Die Bilddatei im SharePoint-Dateisystem.|  
    |SitePages_|Die Seite.|  
  
3.  Wählen Sie die **Fertig stellen** Schaltfläche, um die ausgewählten Elemente zu importieren.  
  
4.  In **Projektmappen-Explorer**, wählen Sie die _catalogsmasterpage\_ Knoten, und legen Sie den Wert von dessen **Bereitstellungskonfliktlösung** Eigenschaft, um **automatische**.  
  
     Damit wird sichergestellt, dass alle Bereitstellungskonflikte automatisch aufgelöst werden.  
  
5.  Verfügt die neue Masterseite den gleichen Namen wie eine Seite, stellen Sie sicher, dass die vorhandene Seite als eine Standardgestaltungsvorlage oder einer benutzerdefinierten Gestaltungsvorlage in SharePoint Designer nicht markiert ist.  
  
     Wenn eine vorhandene Gestaltungsvorlage als Standardgestaltungsvorlage oder benutzerdefinierte Gestaltungsvorlage gekennzeichnet ist, erhalten Sie einen Fehler bei der Bereitstellung, der besagt, dass die Gestaltungsvorlage kann nicht gelöscht werden. Zur Vermeidung dieses Problems folgendermaßen Sie vor:  
  
    -   Wenn die vorhandene Gestaltungsvorlage als Standardgestaltungsvorlage festgelegt ist, legen Sie vorübergehend eine andere Gestaltungsvorlage als Standardgestaltungsvorlage. Nachdem Sie die Dateien in SharePoint bereitstellen, legen Sie die neue Masterseite als Standardgestaltungsvorlage.  
  
    -   Wenn die vorhandene Gestaltungsvorlage als benutzerdefinierte Gestaltungsvorlage festgelegt ist, legen Sie vorübergehend eine andere Gestaltungsvorlage als benutzerdefinierte Gestaltungsvorlage. Nachdem Sie die Dateien in SharePoint bereitstellen, legen Sie die neue Masterseite als benutzerdefinierte Gestaltungsvorlage.  
  
6.  Wählen Sie in der Menüleiste **erstellen**, **Projektmappe bereitstellen**.  
  
7.  Öffnen Sie die SharePoint-Website, um die bereitgestellten Elemente anzuzeigen.  
  
 Eine alternative Möglichkeit zum Importieren von Dateien in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und zur Weitergabe an SharePoint besteht im Hinzufügen von Dateien in Module in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Vorgehensweise: Importieren einer Masterseite oder Design](../sharepoint/how-to-import-a-master-page-or-theme.md) und [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  