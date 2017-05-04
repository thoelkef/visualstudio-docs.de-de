---
title: "Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit Bild | Microsoft Docs"
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
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit Bild
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie eine benutzerdefinierte SharePoint\-Gestaltungsvorlage und eine Websiteseite mit einem Bild in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Projekt importiert werden.  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie die folgenden Aufgaben ausgeführt werden:  
  
-   Erstellen einer benutzerdefinierten Gestaltungsvorlage und einer Websiteseite mit einem Bild in SharePoint Designer.  
  
-   Exportieren einer benutzerdefinierten Gestaltungsvorlage, eines Bilds und einer Websiteseite in eine SharePoint\-Lösungsdatei \(WSP\-Datei\).  
  
-   Importieren und Bereitstellen der WSP\-Datei in einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Projekt mit dem Projekt "SharePoint\-Lösungspaket importieren".  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise sind folgende Komponenten erforderlich:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## Erstellen von Elementen in SharePoint Designer  
 In diesem Beispiel wird gezeigt, wie drei Elemente in SharePoint Designer für den Export erstellt werden: eine benutzerdefinierte Gestaltungsvorlage, eine Websiteseite, die auf die benutzerdefinierte Gestaltungsvorlage verweist, und eine Bilddatei, die auf der Websiteseite angezeigt wird.  Das Bild wird dem Ordner "\/images\/" in SharePoint hinzugefügt.  
  
#### So erstellen Sie eine benutzerdefinierte Gestaltungsvorlage in SharePoint Designer  
  
1.  im SharePoint Designer im Navigationsbereich, wählen Sie das **Masterseiten** Site\-Objekt aus.  
  
2.  Klicken Sie im Menüband **Masterseiten** wählen Sie **Leere Gestaltungsvorlage** aus.  
  
3.  Wählen Sie die neue Masterseite, und dann, auf dem Menüband **Masterseiten** aus, wählen Sie **Datei bearbeiten** aus.  
  
4.  Klicken Sie unten in SharePoint Designer auf die Registerkarte **Code** aus.  
  
5.  Ersetzen Sie das vorhandene Markup durch folgendes Markup:  
  
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
  
6.  Speichern Sie die Seite, wählen Sie die Registerkarte **Masterseiten** aus und geben Sie der Masterseite in **mybasic1.master** um.  
  
## Hinzufügen eines Bilds zur Inhaltsdatenbank in SharePoint Designer  
 Jetzt können Sie ein Bild hinzufügen, das auf der Websiteseite angezeigt werden soll.  Das Bild wird in der SharePoint\-Inhaltsdatenbank bereitgestellt.  
  
#### So fügen Sie ein Bild zur Inhaltsdatenbank in SharePoint Designer hinzu  
  
1.  im Navigationsbereich wählen Sie das **Alle Dateien** Site\-Objekt, und dann in der Strukturansicht, den Ordner **Bilder** aus.  
  
2.  Klicken Sie im Menüband **Alle Dateien** wählen Sie **Dateien importieren** aus, wählen Sie eine Datei aus, und wählen Sie dann die Schaltfläche **OK** aus.  In diesem Beispiel wird die Datei **myimg1.png** genannt.  
  
     Optional können Sie einen Unterordner erstellen, um die Bilder besser zu organisieren.  
  
3.  Schließen Sie das Dialogfeld **Importieren**.  
  
## Erstellen einer Websiteseite  
 Diese grundlegende Websiteseite verwendet die benutzerdefinierte Gestaltungsvorlage und zeigt das Bild an, das Sie im vorherigen Schritt hinzugefügt haben.  
  
#### So erstellen Sie eine Websiteseite  
  
1.  im Navigationsbereich wählen Sie das Objekt **Websiteseiten** aus.  
  
2.  Klicken Sie im Menüband **Seiten** wählen Sie die Schaltfläche **Seite** aus, wählen Sie den Seitentyp **ASPX** aus, und nennen Sie die neue Datei **mycontentpage1.aspx**.  
  
     Optional können Sie einen Unterordner erstellen, um die Websiteseiten besser zu organisieren.  
  
3.  In den Websiteseiten übernehmen, wählen **MyContentPage1.aspx**, um die Eigenschaftenseite, und klicken Sie dann am unteren Rand der Seite zu öffnen, den Link **Datei bearbeiten**.  
  
     Wenn eine Meldung und wird angezeigt, dass diese Seite keine Bereiche enthält, die im abgesicherten Modus bearbeitbar sind und fragt, ob Sie diese Seite im erweiterten Modus öffnen möchten, wählen Sie die Schaltfläche **Ja** aus.  
  
4.  Am unteren Rand der Seite auf die Schaltfläche **Code** aus.  
  
5.  Ersetzen Sie das vorhandene Markup durch folgendes Markup:  
  
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
  
## Exportieren der Elemente aus SharePoint  
 Exportieren Sie die Elemente aus SharePoint in eine SharePoint\-Lösungsdatei \(WSP\-Datei\).  
  
#### So exportieren Sie Elemente aus SharePoint Designer  
  
1.  im SharePoint Designer im Navigationsbereich, wählen Sie das Objekt **Teamwebsite**, und klicken Sie dann im Menüband **Site**, **Als Vorlage speichern** aus.  
  
2.  Im Dialogfeld **Als Vorlage speichern** geben Sie einen Dateinamen und einen Vorlagennamen ein, aktivieren Sie das Kontrollkästchen **Inhalte einschließen** und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Dies speichert den Inhalt der Website in der WSP\-Datei.  
  
3.  Nachdem die Projektmappe exportiert, wählen Sie den Link **Lösungskatalog**, um die Liste der verfügbaren Projektmappendateien anzuzeigen.  
  
4.  Öffnen Sie das Kontextmenü für die neue WSP\-Datei, und wählen Sie dann **Ziel speichern unter**, um sie an das System zu speichern.  
  
## Importieren der Elemente in Visual Studio  
 Importieren Sie die WSP\-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Nachdem der Inhalt importiert wurde, können Sie ihn anpassen, weitere Elemente hinzufügen und den Inhalt dann bereitstellen.  
  
#### So importieren Sie Elemente aus der WSP\-Datei in Visual Studio  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Projekt **SharePoint 2010\-Lösungspaket importieren**.  
  
2.  Auf der Seite **Zu importierende Elemente auswählen** unter **Modul** in der Spalte **Typ**, aktivieren Sie die Kontrollkästchen für die Dateien in der folgenden Tabelle für den Import aus.  
  
    |Dateiname|**Beschreibung**|  
    |---------------|----------------------|  
    |\_catalogsmasterpage\_|Die benutzerdefinierte Gestaltungsvorlage.|  
    |images\_|Die Bilddatei im SharePoint\-Dateisystem.|  
    |SitePages\_|Die Websiteseite.|  
  
3.  Wählen Sie die Schaltfläche **Fertig stellen**, um die ausgewählten Elemente zu importieren.  
  
4.  Wählen Sie im **Projektmappen\-Explorer** den \_catalogsmasterpage\_ Knoten, und legen Sie den Wert der Eigenschaft **Bereitstellungskonfliktlösung** auf **Automatisch** fest.  
  
     Damit wird sichergestellt, dass alle Bereitstellungskonflikte automatisch gelöst werden.  
  
5.  Wenn die neue Gestaltungsvorlage den gleichen Namen wie eine vorhandene Seite hat, stellen Sie sicher, dass die vorhandene Seite in SharePoint Designer nicht als Standardgestaltungsvorlage oder benutzerdefinierte Gestaltungsvorlage gekennzeichnet ist.  
  
     Wenn eine vorhandene Gestaltungsvorlage als Standardgestaltungsvorlage oder benutzerdefinierte Gestaltungsvorlage gekennzeichnet ist, wird ein Bereitstellungsfehler mit dem Hinweis ausgegeben, dass die Gestaltungsvorlage nicht gelöscht werden kann.  Um dieses Problem zu vermeiden, gehen Sie wie folgt vor:  
  
    -   Wenn die vorhandene Gestaltungsvorlage als Standardgestaltungsvorlage festgelegt ist, legen Sie vorübergehend eine andere Gestaltungsvorlage als Standardgestaltungsvorlage fest.  Nachdem Sie die Dateien auf SharePoint bereitgestellt haben, legen Sie die neue Gestaltungsvorlage als Standardgestaltungsvorlage fest.  
  
    -   Wenn die vorhandene Gestaltungsvorlage als benutzerdefinierte Gestaltungsvorlage festgelegt ist, legen Sie vorübergehend eine andere Gestaltungsvorlage als benutzerdefinierte Gestaltungsvorlage fest.  Nachdem Sie die Dateien auf SharePoint bereitgestellt haben, legen Sie die neue Gestaltungsvorlage als benutzerdefinierte Gestaltungsvorlage fest.  
  
6.  Wählen Sie in der Menüleiste **Projektmappe bereitstellen**, **Erstellen** aus.  
  
7.  Öffnen Sie die SharePoint\-Website, um die bereitgestellten Elemente anzuzeigen.  
  
 Eine alternative Art, Dateien in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zu importieren und sie auf SharePoint bereitzustellen, besteht darin, die Dateien in Module in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hinzuzufügen.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Gewusst wie: Erstellen einer Masterseite oder eines Designs](../sharepoint/how-to-import-a-master-page-or-theme.md) und [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  