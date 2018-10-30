---
title: Anpassung der Office-Benutzeroberfläche
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48c7fe1948231f88aba8309d6d06186848d32455
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836763"
---
# <a name="office-ui-customization"></a>Anpassung der Office-Benutzeroberfläche
  Sie können die Benutzeroberfläche (UI) von Microsoft Office-Anwendungen anpassen, indem Sie die Office Developer Tools in Visual Studio verwenden. In diesem Thema werden die Funktionen der Benutzeroberfläche, die Sie anpassen können, in den folgenden Abschnitten beschrieben:  
  
-   [Vergleich der Funktionen der Benutzeroberfläche](#Comparison)  
  
-   [Aktionsbereiche und benutzerdefinierte Aufgabenbereiche](#Actions)  
  
-   [Benutzerdefinierte Multifunktionsleisten-Benutzeroberfläche](#Ribbon)  
  
-   [Backstage-Ansicht](#Backstage)  
  
-   [Outlook-Formularbereichen](#FormRegion)  
  
-   [Steuerelemente in Dokumenten](#Controls)  
  
-   [Kontextmenüs](#Shortcut)  
  
##  <a name="Comparison"></a> Vergleich der Funktionen der Benutzeroberfläche  
 In der folgenden Tabelle werden die wichtigsten Funktionen der Benutzeroberfläche verglichen, die Sie in Microsoft Office-Projekten anpassen können.  
  
|Feature|Unterstützte Projekttypen|Unterstützte Microsoft Office-Anwendungen|  
|-------------|-----------------------------|---------------------------------------------|  
|Aktionsbereich|Anpassungen auf Dokumentebene|Excel<br /><br /> Word|  
|Benutzerdefinierte Aufgabenbereiche|VSTO-Add-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Benutzerdefinierte Menüband-Benutzeroberfläche|Anpassungen auf Dokumentebene<br /><br /> VSTO-Add-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Backstage-Ansicht|Anpassungen auf Dokumentebene<br /><br /> VSTO-Add-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Outlook-Formularbereiche|VSTO-Add-Ins|Outlook|  
|Steuerelemente in Dokumenten|Anpassungen auf Dokumentebene<br /><br /> VSTO-Add-Ins|Excel<br /><br /> Word|  
|Kontextmenüs|Anpassungen auf Dokumentebene<br /><br /> VSTO-Add-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Aktionsbereiche und benutzerdefinierte Aufgabenbereiche  
 Aufgabenbereiche sind Bereiche der Benutzeroberfläche, die in einer Microsoft Office-Anwendung normalerweise auf einer Seite eines Fensters angedockt sind. Fast alle Microsoft Office-Anwendungen enthalten integrierte Aufgabenbereiche. Ein Beispiel für einen Aufgabenbereich ist der Hilfe-Aufgabenbereich in Word.  
  
 Die Office-Entwicklungstools in Visual Studio bieten zwei unterschiedliche Wege zum Anpassen von Aufgabenbereichen:  
  
- Sie können einen Aktionsbereich einer Anpassung auf Dokumentebene hinzufügen. Standardmäßig wird der Aktionsbereich auf der rechten Seite der Anwendung (rechts vom Dokument) angezeigt. Der Aktionsbereich kann im Dokument aber auch links, oben oder unten angezeigt werden.  
  
- Sie können einen benutzerdefinierten Aufgabenbereich einem VSTO-Add-In hinzufügen. Benutzer können benutzerdefinierte Aufgabenbereiche an verschiedene Seiten des Anwendungsfensters andocken, oder sie können benutzerdefinierte Aufgabenbereiche an eine beliebige Position im Fenster ziehen.  
  
  Mit Aktionsbereichen und benutzerdefinierten Aufgabenbereichen werden Funktionen bereitgestellt, indem viele verschiedene Steuerelemente in den Bereichen enthalten sind, die Benutzer bei Aufgaben unterstützen, z. B. der Dateneingabe. Im Vergleich zu einer Menübandgruppe ermöglichen Aktionsbereiche und benutzerdefinierte Aufgabenbereiche eine deutlich größere Fläche für Text und Steuerelemente.  
  
  Weitere Informationen zu Aktionsbereichen finden Sie unter [aktionsbereichsübersicht](../vsto/actions-pane-overview.md). Weitere Informationen zu benutzerdefinierten Aufgabenbereichen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Benutzerdefinierte Multifunktionsleisten-Benutzeroberfläche  
 Sie können die Menüband-Benutzeroberfläche so anpassen, dass Funktionen bereitgestellt werden, die Sie Anwendungen in Office hinzufügen. Das Menüband dient zum Organisieren von verwandten Befehlen (in Form von Steuerelementen), damit sie leichter zu finden sind. Sie können Ihre eigenen Menübandregisterkarten und -gruppen erstellen, um Benutzern Zugriff auf Funktionen zu gewähren, die Sie in Ihrer Projektmappe bereitstellen. Auf die meisten Funktionen, auf die in früheren Versionen des Microsoft Office-Systems über die Menüs und Symbolleisten zugegriffen wurde, kann jetzt über das Menüband zugegriffen werden.  
  
 Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Backstage-Ansicht  
 In Office-Anwendungen auf die **Datei** Registerkarte wird die Backstage-Ansicht geöffnet. In der Backstage-Ansicht sind Aufgaben und Aktionen der Dateiebene kombiniert. Sie ersetzt ähnliche Funktionen, die im Microsoft Office-System 2007 über die Microsoft Office-Schaltfläche zugänglich waren. Die Backstage-Ansicht ist per XML vollständig erweiterbar.  
  
 In Visual Studio werden kein Designer bzw. keine APIs zum Anpassen der Backstage-Ansicht bereitgestellt. Jedoch wenn Sie beim Hinzufügen einer **Menüband (XML)** Element Office-Projekt, können Sie XML in der Menüband-XML-Datei zum Anpassen der Backstage-Ansicht hinzufügen. Weitere Informationen zu **Menüband (XML)** Elemente finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
 Weitere Informationen zum Anpassen der Backstage-Ansicht finden Sie unter [Einführung in die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182189) und [anpassen die Office 2010-Backstage-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Outlook-Formularbereichen  
 Verwenden Sie Formularbereiche, um standardmäßigen Microsoft Office Outlook-Formularen benutzerdefinierte Funktionen hinzuzufügen. Sie können Formularbereiche erstellen, mit denen beliebige vorhandene Formulare um zusätzliche Felder oder Steuerelemente erweitert werden. Wenn Sie mit den Office-Entwicklungstools in Visual Studio einen neuen Formularbereich erstellen, können Sie im Formularbereich nur Windows Forms-Steuerelemente verwenden. Wenn Sie einen Formularbereich importieren, der in Outlook entworfen wurde, können Sie nur systemeigene Outlook-Steuerelemente verwenden.  
  
 Sie können Formularbereiche erstellen, die verschiedene Bereiche der Outlook-Benutzeroberfläche einnehmen. Benachbarte Formularbereiche werden beispielsweise unten auf der ersten Seite eines Formulars angezeigt, und jeder benachbarte Formularbereich ist reduzierbar. Sie können auch einen separaten Formularbereich hinzufügen, der als vollständige zusätzliche Formularseite angezeigt wird und in allen vorhandenen Standardformularen oder benutzerdefinierten Formularen verwendet werden kann.  
  
 Weitere Informationen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Steuerelemente in Dokumenten  
 Sie können Word-Dokumenten und Excel-Arbeitsblättern viele verschiedene Steuerelemente hinzufügen. Es kann beispielsweise sein, dass Sie einem Dokument ein Steuerelement für die Datumsauswahl hinzufügen möchten, damit Benutzer Datumsangaben im Standardformat eingeben können, oder dass Sie eine Schaltfläche in ein Arbeitsblatt einfügen möchten, mit dem Daten an eine Datenbank gesendet werden können.  
  
 Wenn Sie Projekte auf Dokumentebene für Excel oder Word entwickeln, können Sie Visual Studio-Designer Steuerelemente in das Dokument oder die Arbeitsmappe in Ihrem Projekt zur Entwurfszeit hinzufügen, oder Sie können Steuerelemente programmgesteuert zur Laufzeit hinzufügen. Wenn Sie VSTO-Add-in-Projekte für Excel oder Word entwickeln, können Sie auf allen geöffneten Dokumenten oder Arbeitsmappen zur Laufzeit programmgesteuert Steuerelemente hinzufügen.  
  
 Weitere Informationen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md) und [Windows forms-Steuerelemente in der Übersicht über Office-Dokumente](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Kontextmenüs  
 Ein Kontextmenü wird angezeigt, wenn Sie in einem Dokument oder einem Anwendungsfenster mit der rechten Maustaste klicken. Sie können festlegen, dass nach dem Eintreten eines Ereignisses ein Kontextmenü angezeigt wird, z. B. nach dem Rechtsklick eines Benutzers auf ein Dokument, eine Arbeitsmappe oder ein Hoststeuerelement. Sie können einem Kontextmenü verschiedene andere Menübefehle oder Steuerelemente hinzufügen. Erstellen von Kontextmenüs mithilfe von XML Wenn Sie beim Hinzufügen einer **Menüband (XML)** Element Office-Projekt, können Sie die Menüband-XML-Datei zum Erstellen von Kontextmenüs XML hinzufügen. Weitere Informationen zur Verwendung von XML zum Erstellen von Kontextmenüs finden Sie unter [Vorgehensweise: Hinzufügen von Befehlen zu Kontextmenüs](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Windows forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Verwenden von WPF-Steuerelemente in Office-Projektmappen](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Gewusst wie: Anzeigen-Add-in-Benutzeroberflächenfehler](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Exemplarische Vorgehensweise: Sammeln von Daten mit einem Windows form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  