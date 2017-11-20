---
title: 'Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website | Microsoft Docs'
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 602615426a8aeca118f6faba65e21778136b0ce6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website
  Diese exemplarische Vorgehensweise veranschaulicht, wie zum Importieren von Elementen aus einer vorhandenen SharePoint-Website in einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Anpassen einer SharePoint-Websites durch das Hinzufügen einer benutzerdefinierten Websitespalte (auch bekannt als ein *Feld*.  
  
-   Exportieren einer SharePoint-Websites als WSP-Datei.  
  
-   Importieren von WSP-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint mithilfe der WSP-Import-Projekt.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="customizing-a-sharepoint-site"></a>Anpassen einer SharePoint-Website  
 In diesem Beispiel erstellt und eine SharePoint-Unterwebsite anpassen, indem eine neue Websitespalte hinzugefügt und erstellen eine andere Unterwebsite zur späteren Verwendung. Sie werden später die erste Unterwebsite in der WSP-Datei exportieren und importieren Sie die benutzerdefinierte Websitespalte in die zweite Unterwebsite mithilfe der WSP-Import-Projekt.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Zum Erstellen und Anpassen einer SharePoint-Websites  
  
1.  Öffnen Sie eine SharePoint-Website mithilfe eines Webbrowsers, wie z. B. http://*Systemname*/SitePages/Home.aspx.  
  
2.  Erstellen Sie eine Unterwebsite außerhalb der SharePoint-Website öffnen die **Websiteaktionen** Menü, und drücken Sie dann die **neuen Standort**.  
  
3.  Auf der Website **erstellen** Dialogfeld Wählen Sie die **leere Website** Typ.  
  
4.  In der **Titel** Geben Sie **Site Column Test 1**, in der **URL-Name** Geben Sie **"columntest1"**; lassen Sie die anderen Einstellungen an Standardeinstellung Werte; und wählen Sie dann die **erstellen** Schaltfläche.  
  
5.  Nachdem die Website erstellt wurde, navigieren Sie im Browser zurück auf der Hauptwebsite http://*Systemname*/SitePages/Home.aspx.  
  
6.  Erstellen Sie eine leere Unterwebsite der SharePoint-Website erneut öffnen die **Websiteaktionen** im Menü auswählen **neuen Standort**, und drücken Sie dann die **leere Website** Typ.  
  
7.  In der **Titel** Geben Sie **Site Column Test 2**, in der **URL-Name** Geben Sie **"columntest2"**; lassen Sie die anderen Einstellungen an Standardeinstellung Werte; und wählen Sie dann die **erstellen** Schaltfläche.  
  
8.  Navigieren Sie zurück zur ersten Unterwebsite, http://*SystemName*/columntest1/default.aspx.  
  
9. Auf der **Websiteaktionen** Menü Wählen Sie **Standorteinstellungen** auf der Seite "Siteeinstellungen" angezeigt.  
  
10. In der **Galerien** Abschnitt der **Site Spalten** Link.  
  
11. Am oberen Rand der **Spalte Websitekatalog** Seite, und wählen Sie die **erstellen** Schaltfläche.  
  
12. In der **Spaltenname** geben **Spalte Test**, behalten die anderen Standardwerte, und wählen Sie dann die **OK** Schaltfläche.  
  
13. Die **Spalte Test** Spalte wird angezeigt, in den Spalten, benutzerdefinierten Überschrift im Katalog Website-Spalte.  
  
## <a name="exporting-the-sharepoint-site"></a>Exportieren die SharePoint-Website  
 Rufen Sie danach eine SharePoint-Setup (.wsp)-Datei mit dem SharePoint-Elemente und Elemente, die Sie in importieren möchten Ihre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt. Wenn Sie nicht bereits über eine WSP-Datei verfügen, müssen Sie eine aus einer vorhandenen SharePoint-Website erstellen. In diesem Beispiel werden Sie die standardmäßige SharePoint-Website in der WSP-Datei exportieren.  
  
> [!IMPORTANT]  
>  Wenn Sie einen Laufzeitfehler des folgenden Verfahrens erhalten, müssen Sie das Verfahren auf einem System ausführen, die auf der SharePoint-Website zugreifen.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>So exportieren Sie eine vorhandene SharePoint-Website  
  
1.  Wählen Sie in der SharePoint-Website **Standorteinstellungen** auf die **Websiteaktionen** Registerkarte, um die Seite "Siteeinstellungen" anzuzeigen.  
  
2.  In der **Websiteaktionen** Abschnitt der Seite Siteeinstellungen, wählen Sie die **speichern Website als Vorlage** Link.  
  
3.  In der **Dateiname** Geben Sie **ExampleSite**, und klicken Sie in der **Vorlagennamen** geben **Beispiel Website**.  
  
4.  Lassen Sie in diesem Beispiel die **Inhalte** Kontrollkästchen deaktivieren.  
  
     Wenn Sie dieses Kontrollkästchen aktivieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] speichert alle Listen und Dokumentbibliotheken und deren Inhalt der WSP-Datei. Obwohl dies in einigen Fällen nützlich ist, ist es nicht erforderlich, damit dieses Beispiel.  
  
5.  Wenn der Vorgang erfolgreich abgeschlossen wurde, wählen Sie die **Lösungskatalog** Link, um die WSP-Datei anzuzeigen.  
  
     Zum Anzeigen der Solutions Gallery Seite höher, öffnen die **Websiteaktionen** im Menü Wählen Sie **Standorteinstellungen**, wählen Sie die **Gehe zu Einstellungen des Standorts auf höchster Ebene** wiederherstellungsverknüpfung in der  **Auflistung standortverwaltung** Abschnitt, und wählen Sie dann die **Lösungen** wiederherstellungsverknüpfung in der **Galerien** Abschnitt.  
  
6.  Wählen Sie in der Solutions Gallery, die **ExampleSite** Link.  
  
7.  In der **Dateidownload** Dialogfeld Wählen Sie die **speichern** Schaltfläche, um die Datei auf dem lokalen System standardmäßig im Ordner "Downloads" zu speichern.  
  
## <a name="importing-the-wsp-file"></a>Die WSP-Datei importieren  
 Importieren Sie nun die WSP-Datei, die ein Element, die Sie wiederverwenden möchten enthält, (die benutzerdefinierte Websitespalte Test-Spalte), die WSP-Datei, um darauf zuzugreifen.  
  
#### <a name="to-import-a-wsp-file"></a>Zum Importieren von WSP-Datei  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld). Wenn die IDE für die Verwendung von Visual Basic-entwicklungseinstellungen auf der Menüleiste festgelegt ist, wählen Sie **Datei**, **neues Projekt**.  
  
2.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  Wählen Sie die **SharePoint 2010-Lösungspaket importieren** Vorlage in der **Vorlagen** , lassen Sie den Namen des Projekts als WspImportProject1, und wählen Sie dann die **OK** Schaltfläche ".  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
4.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** geben die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für den zweiten SharePoint-Unterwebsite, die Sie zuvor erstellt haben. Fügen Sie der neuen benutzerdefinierten Feld item, http://*Systemname*/columntest2, um diese Unterwebsite.  
  
5.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt, lassen Sie die Auswahl als **bereitstellen als sandkastenlösung**.  
  
6.  In der **Geben Sie die Projektquelle der neuen** Seite, navigieren Sie zum Speicherort auf dem System, in dem Sie die WSP-Datei zuvor gespeichert, und wählen Sie dann die **Weiter** Schaltfläche.  
  
    > [!NOTE]  
    >  Bei Auswahl der **Fertig stellen** Schaltfläche auf dieser Seite werden alle verfügbaren Elemente in der WSP-Datei importiert werden.  
  
7.  In der **Elemente auswählen, um importieren** Feld, das Aufheben der Auswahl der Kontrollkästchen in der Liste mit Ausnahme von **Spalte Test**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Da die Liste viele Elemente enthält, können Sie auswählen, die STRG + A-Taste, um alle Elemente in der Liste ausgewählt werden. Wählen Sie die LEERTASTE, um alle Kontrollkästchen zu deaktivieren, und wählen Sie nur das Kontrollkästchen neben den **Spalte Test** Element.  
  
     Nachdem der Importvorgang abgeschlossen ist, wird ein neues Projekt mit dem Namen **WspImportProject1** erstellt wird, enthält einen Ordner namens **Felder**. In diesem Ordner wird die benutzerdefinierte Websitespalte **Spalte Test** und die zugehörige Definitionsdatei "Elements.xml".  
  
## <a name="deploying-the-project"></a>Beim Bereitstellen des Projekts  
 Stellen Sie abschließend **WspImportProject1** an den zweiten SharePoint Unterwebsite, die Sie zuvor an die benutzerdefinierte Websitespalte erstellt.  
  
#### <a name="to-deploy-the-project"></a>Bereitstellung des Projekts  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie die F5-Taste zum Bereitstellen und Ausführen der WSP-Import-Projekt.  
  
2.  Öffnen Sie auf der SharePoint-Website die **Websiteaktionen** Menü, und wählen Sie dann **Standorteinstellungen** auf der Seite "Siteeinstellungen" angezeigt.  
  
3.  In der **Galerien** Abschnitt der **Site Spalten** Link.  
  
4.  Führen Sie einen Bildlauf nach unten, um die **benutzerdefinierte Spalten** Abschnitt.  
  
     Beachten Sie, dass die benutzerdefinierte Websitespalte, die Sie importiert haben, aus der ersten SharePoint-Website in der Liste angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  