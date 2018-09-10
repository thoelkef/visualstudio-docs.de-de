---
title: 'Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: 2d9542e14f41722a2f339bfac5c3353dc2e89263
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635465"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Importieren von Elementen aus einer vorhandenen SharePoint-Website in einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Anpassen von einer SharePoint-Website durch eine benutzerdefinierte Spalte hinzufügen (auch bekannt als eine *Feld*.  
  
-   Eine SharePoint-Website exportiert in eine WSP-Datei.  
  
-   Importieren von WSP-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint mithilfe der WSP-Projekt importieren.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  
  
-   Visual Studio.  
  
## <a name="customize-a-sharepoint-site"></a>Anpassen einer SharePoint-Websites
 In diesem Beispiel werden Sie erstellen und Anpassen eine SharePoint-Unterwebsite, indem eine neue Websitespalte hinzugefügt wird und erstellen eine weitere Unterwebsite zur späteren Verwendung. Sie werden später erste Unterwebsite in eine WSP-Datei exportieren und dann die benutzerdefinierte Website-Spalte in die zweite Unterwebsite mit dem WSP-Import-Projekt importieren.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Zum Erstellen und Anpassen einer SharePoint-Websites  
  
1.  Öffnen Sie eine SharePoint-Website mithilfe eines Webbrowsers, wie z. B. http://*Systemname*  /SitePages/Home.aspx.  
  
2.  Erstellen eine Unterwebsite auf der SharePoint-Website öffnen die **Websiteaktionen** Menü auswählen und dann **neuen Standort**.  
  
3.  In der Website **erstellen** Dialogfeld auf die **Blank Site** Typ.  
  
4.  In der **Titel** geben **Site Column Test 1**, in der **URL-Name** Geben Sie **"columntest1"**; behalten Sie die anderen Einstellungen für ihren Standardwert -Werte und wählen Sie dann die **erstellen** Schaltfläche.  
  
5.  Nachdem die Website erstellt wurde, navigieren Sie im Browser an den zentralen Standort http://*Systemname*  /SitePages/Home.aspx.  
  
6.  In diesem Fall eine leere Unterwebsite der SharePoint-Website erstellen möchten, öffnen die **Websiteaktionen** im Menü auswählen **neuen Standort**, und wählen Sie dann die **Blank Site** Typ.  
  
7.  In der **Titel** geben **Site Column Test 2**, in der **URL-Name** Geben Sie **"columntest2"**; behalten Sie die anderen Einstellungen für ihren Standardwert -Werte und wählen Sie dann die **erstellen** Schaltfläche.  
  
8.  Navigieren Sie zurück zur ersten Unterwebsite, http://*SystemName*/columntest1/default.aspx.  
  
9. Auf der **Websiteaktionen** Menü wählen **Standorteinstellungen** auf die Seite Siteeinstellungen anzeigen.  
  
10. In der **Galerien** Abschnitt der **Site Spalten** Link.  
  
11. Am oberen Rand der **Spalte Websitekatalog** Seite die **erstellen** Schaltfläche.  
  
12. In der **Spaltenname** geben **Spalte Test**, behalten die anderen Standardwerte, und wählen Sie dann die **OK** Schaltfläche.  
  
13. Die **Spalte Test** Spalte wird in den Spalten, die benutzerdefinierte Überschrift in der Spalte-Websitekatalog.  
  
## <a name="exporting-the-sharepoint-site"></a>Exportieren die SharePoint-Website
 Als Nächstes erhalten Sie eine SharePoint-Setup (.wsp)-Datei mit dem SharePoint-Elemente und Elemente, die Sie in importieren möchten Ihre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt. Wenn Sie nicht bereits über eine WSP-Datei verfügen, müssen Sie eine aus einer vorhandenen SharePoint-Website erstellen. In diesem Beispiel werden Sie der Standard-SharePoint-Website in eine WSP-Datei exportieren.  
  
> [!IMPORTANT]  
>  Wenn Sie einen Laufzeitfehler, die den folgenden Schritten erhalten haben, müssen Sie das Verfahren auf einem System ausführen, die zur SharePoint-Website zugreifen.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>So exportieren Sie eine vorhandene SharePoint-Website  
  
1.  Wählen Sie in der SharePoint-Website **Standorteinstellungen** auf die **Websiteaktionen** Tab, um die Seite Siteeinstellungen anzeigen.  
  
2.  In der **Websiteaktionen** Abschnitt wählen Sie die Seite Siteeinstellungen der **speichern-Website als Vorlage** Link.  
  
3.  In der **Dateiname** geben **ExampleSite**, und klicken Sie in der **Vorlagennamen** Geben Sie **Beispielwebsite**.  
  
4.  In diesem Beispiel lassen den **Inhalte einschließen** Kontrollkästchen deaktivieren.  
  
     Wenn Sie dieses Kontrollkästchen aktivieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] speichert Sie in der .wsp-Datei alle Listen und Dokumentbibliotheken und ihren Inhalt zu. Obwohl dies unter bestimmten Umständen nützlich ist, ist es nicht für dieses Beispiel erforderlich.  
  
5.  Wenn der Vorgang erfolgreich abgeschlossen wurde, wählen Sie die **Lösungskatalog** Link, um die .wsp-Datei anzuzeigen.  
  
     Zum Anzeigen der Solutions Gallery Seite höher, öffnen die **Websiteaktionen** im Menü wählen **Standorteinstellungen**, wählen Sie die **wechseln Sie zu Einstellungen des Standorts auf höchster Ebene** -link in der  **Verwaltung der Websitesammlung** aus, und wählen Sie dann die **Lösungen** -link in der **Galerien** Abschnitt.  
  
6.  Wählen Sie im Lösungskatalog der **ExampleSite** Link.  
  
7.  In der **Dateidownload** Dialogfeld auf die **speichern** aus, um die Datei auf Ihrem lokalen System standardmäßig im Ordner "Downloads" zu speichern.  
  
## <a name="import-the-wsp-file"></a>Die WSP-Datei importieren
 Nun, Sie haben eine *.wsp* -Datei, die ein Element, die Sie möchten enthält (die benutzerdefinierte Spalte Test-Spalte) wiederverwenden, importieren die *.wsp* Datei für den Zugriff.  
  
#### <a name="to-import-a-wsp-file"></a>Um eine WSP-Datei zu importieren.  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt**Dialogfeld. Wenn Ihre IDE auf der Menüleiste mit Visual Basic-entwicklungseinstellungen festgelegt ist, wählen Sie **Datei** > **neues Projekt**.  
  
2.  Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  Wählen Sie die **SharePoint 2010-Lösungspaket importieren** Vorlage in der **Vorlagen** , lassen Sie den Namen des Projekts als WspImportProject1, und wählen Sie dann die **OK** Schaltfläche ".  
  
     Die **SharePoint Customization Wizard** angezeigt wird.  
  
4.  Auf der **Geben Sie die Website und Sicherheitsebene für debugging** geben die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für den zweiten SharePoint-Unterwebsite, die Sie zuvor erstellt haben. Fügen Sie die neue benutzerdefinierte Feld, http://*Systemname*/columntest2, um diese Unterwebsite.  
  
5.  In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt, ändern Sie die Auswahl **als sandkastenlösung bereitstellen**.  
  
6.  In der **neue Projektquelle angeben** Seite, navigieren Sie zum Speicherort auf dem System, in dem Sie gespeichert haben, die *.wsp* Datei zuvor aus, und wählen Sie dann die **Weiter** Schaltfläche.  
  
    > [!NOTE]  
    >  Bei Auswahl der **Fertig stellen** Schaltfläche auf dieser Seite, die alle verfügbaren Elemente in der *.wsp* Datei importiert werden soll.  
  
7.  In der **zu importierende Elemente auswählen** Deaktivieren aller Kontrollkästchen in der Liste mit Ausnahme von **Spalte Test**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Da die Liste viele Elemente enthält, können Sie die **STRG**+**ein** Schlüssel auf alle Elemente in der Liste aus, wählen Sie die LEERTASTE, um alle Kontrollkästchen zu deaktivieren, und wählen Sie dann nur die Überprüfung im Feld neben dem **Spalte Test** Element.  
  
     Nachdem der Importvorgang abgeschlossen ist, wird ein neues Projekt namens **WspImportProject1** erstellt wird, enthält einen Ordner namens **Felder**. In diesem Ordner wird die benutzerdefinierte Websitespalte **Spalte Test** und seine Berichtsdefinitionsdatei *"Elements.xml"*.  
  
## <a name="deploy-the-project"></a>Bereitstellen des Projekts
 Stellen Sie abschließend **WspImportProject1** auf der zweiten SharePoint-Unterwebsite, dass Sie zuvor zum Anzeigen der Spalte für die benutzerdefinierte Website erstellt haben.  
  
#### <a name="to-deploy-the-project"></a>Um das Projekt bereitzustellen  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie die **F5** Schlüssel zum Bereitstellen und Ausführen der *.wsp* Projekt importieren.  
  
2.  Öffnen Sie auf der SharePoint-Website die **Websiteaktionen** Menü, und wählen Sie dann **Standorteinstellungen** auf die Seite Siteeinstellungen anzeigen.  
  
3.  In der **Galerien** Abschnitt der **Site Spalten** Link.  
  
4.  Führen Sie einen Bildlauf nach unten, um die **benutzerdefinierte Spalten** Abschnitt.  
  
     Beachten Sie, dass die benutzerdefinierte Website-Spalte, die Sie importiert haben, aus dem ersten SharePoint-Standort in der Liste angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
