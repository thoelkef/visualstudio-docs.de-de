---
title: "Anpassung der Office-Benutzeroberfl&#228;che | Microsoft Docs"
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
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Erstellen"
  - "Menüs [Office-Entwicklung in Visual Studio], Anpassen"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Benutzeroberflächenanpassung"
  - "Symbolleisten [Office-Entwicklung in Visual Studio], Anpassen"
  - "WPF [Office-Entwicklung in Visual Studio]"
ms.assetid: 3d7c7b88-2053-4ada-bfe7-e7bb202c430b
caps.latest.revision: 74
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 73
---
# Anpassung der Office-Benutzeroberfl&#228;che
  Sie können die Benutzeroberfläche \(UI\) von Microsoft Office\-Anwendungen anpassen, indem Sie die Office Developer Tools in Visual Studio verwenden.  In diesem Thema werden die Features der Benutzeroberfläche, die Sie anpassen können, in den folgenden Abschnitten beschrieben:  
  
-   [Vergleich von Features der Benutzeroberfläche](#Comparison)  
  
-   [Aktionsbereiche und benutzerdefinierte Aufgabenbereiche](#Actions)  
  
-   [Benutzerdefinierte Menüband\-Benutzeroberfläche](#Ribbon)  
  
-   [Backstage\-Ansicht](#Backstage)  
  
-   [Outlook\-Formularbereiche](#FormRegion)  
  
-   [Steuerelemente in Dokumenten](#Controls)  
  
-   [Kontextmenüs](#Shortcut)  
  
##  <a name="Comparison"></a> Vergleich von Features der Benutzeroberfläche  
 In der folgenden Tabelle werden die wichtigsten Features der Benutzeroberfläche verglichen, die Sie in Microsoft Office\-Projekten anpassen können.  
  
|Funktion|Unterstützte Projekttypen|Unterstützte Microsoft Office\-Anwendungen|  
|--------------|-------------------------------|------------------------------------------------|  
|Aktionsbereich|Anpassungen auf Dokumentebene|Excel<br /><br /> Word|  
|Benutzerdefinierte Aufgabenbereiche|VSTO\-Add\-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Benutzerdefinierte Menüband\-Benutzeroberfläche|Anpassungen auf Dokumentebene<br /><br /> VSTO\-Add\-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Backstage\-Ansicht|Anpassungen auf Dokumentebene<br /><br /> VSTO\-Add\-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Outlook\-Formularbereiche|VSTO\-Add\-Ins|Outlook|  
|Steuerelemente in Dokumenten|Anpassungen auf Dokumentebene<br /><br /> VSTO\-Add\-Ins|Excel<br /><br /> Word|  
|Kontextmenüs|Anpassungen auf Dokumentebene<br /><br /> VSTO\-Add\-Ins|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Aktionsbereiche und benutzerdefinierte Aufgabenbereiche  
 Aufgabenbereiche sind Bereiche der Benutzeroberfläche, die in einer Microsoft Office\-Anwendung normalerweise auf einer Seite eines Fensters angedockt sind.  Fast alle Microsoft Office\-Anwendungen enthalten integrierte Aufgabenbereiche.  Ein Beispiel für einen Aufgabenbereich ist der Hilfe\-Aufgabenbereich in Word.  
  
 Die Office\-Entwicklungstools in Visual Studio bieten zwei unterschiedliche Wege zum Anpassen von Aufgabenbereichen:  
  
-   Sie können einen Aktionsbereich einer Anpassung auf Dokumentebene hinzufügen.  Standardmäßig wird der Aktionsbereich auf der rechten Seite der Anwendung \(rechts vom Dokument\) angezeigt.  Der Aktionsbereich kann im Dokument aber auch links, oben oder unten angezeigt werden.  
  
-   Sie können einen benutzerdefinierten Aufgabenbereich einem VSTO\-Add\-In hinzufügen.  Benutzer können benutzerdefinierte Aufgabenbereiche an verschiedene Seiten des Anwendungsfensters andocken, oder sie können benutzerdefinierte Aufgabenbereiche an eine beliebige Position im Fenster ziehen.  
  
 Mit Aktionsbereichen und benutzerdefinierten Aufgabenbereichen werden Funktionen bereitgestellt, indem viele verschiedene Steuerelemente in den Bereichen enthalten sind, die Benutzer bei Aufgaben unterstützen, z. B. der Dateneingabe.  Im Vergleich zu einer Menübandgruppe ermöglichen Aktionsbereiche und benutzerdefinierte Aufgabenbereiche eine deutlich größere Fläche für Text und Steuerelemente.  
  
 Weitere Informationen zu Aktionsbereichen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  Weitere Informationen zu benutzerdefinierten Aufgabenbereichen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Benutzerdefinierte Menüband\-Benutzeroberfläche  
 Sie können die Menüband\-Benutzeroberfläche so anpassen, dass Funktionen bereitgestellt werden, die Sie Anwendungen in Office hinzufügen.  Das Menüband dient zum Organisieren von verwandten Befehlen \(in Form von Steuerelementen\), damit sie leichter zu finden sind.  Sie können Ihre eigenen Menübandregisterkarten und \-gruppen erstellen, um Benutzern Zugriff auf Funktionen zu gewähren, die Sie in Ihrer Projektmappe bereitstellen.  Auf die meisten Features, auf die in früheren Versionen des Microsoft Office\-Systems über die Menüs und Symbolleisten zugegriffen wurde, kann jetzt über das Menüband zugegriffen werden.  
  
 Weitere Informationen finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Backstage\-Ansicht  
 Wenn in Office\-Anwendungen auf die Registerkarte **Datei** geklickt wird, wird die Backstage\-Ansicht geöffnet.  In der Backstage\-Ansicht sind Aufgaben und Aktionen der Dateiebene kombiniert. Sie ersetzt ähnliche Funktionen, die im Microsoft Office\-System 2007 über die Microsoft Office\-Schaltfläche zugänglich waren.  Die Backstage\-Ansicht ist per XML vollständig erweiterbar.  
  
 In Visual Studio werden kein Designer bzw. keine APIs zum Anpassen der Backstage\-Ansicht bereitgestellt.  Wenn Sie dem Office\-Projekt aber ein **Menüband \(XML\)**\-Element hinzufügen, können Sie der Menüband\-XML\-Datei XML\-Code hinzufügen, um die Backstage\-Ansicht anzupassen.  Weitere Informationen zu **Menüband \(XML\)**\-Elementen finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
 Weitere Informationen zum Anpassen der Backstage\-Ansicht finden Sie unter [Einführung in die Office 2010\-Backstage\-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182189) und [Anpassen der Office 2010\-Backstage\-Ansicht für Entwickler](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Outlook\-Formularbereiche  
 Verwenden Sie Formularbereiche, um standardmäßigen Microsoft Office Outlook\-Formularen benutzerdefinierte Funktionen hinzuzufügen.  Sie können Formularbereiche erstellen, mit denen beliebige vorhandene Formulare um zusätzliche Felder oder Steuerelemente erweitert werden.  Wenn Sie mit den Office\-Entwicklungstools in Visual Studio einen neuen Formularbereich erstellen, können Sie im Formularbereich nur Windows Forms\-Steuerelemente verwenden.  Wenn Sie einen Formularbereich importieren, der in Outlook entworfen wurde, können Sie nur systemeigene Outlook\-Steuerelemente verwenden.  
  
 Sie können Formularbereiche erstellen, die verschiedene Bereiche der Outlook\-Benutzeroberfläche einnehmen.  Benachbarte Formularbereiche werden beispielsweise unten auf der ersten Seite eines Formulars angezeigt, und jeder benachbarte Formularbereich ist reduzierbar.  Sie können auch einen separaten Formularbereich hinzufügen, der als vollständige zusätzliche Formularseite angezeigt wird und in allen vorhandenen Standardformularen oder benutzerdefinierten Formularen verwendet werden kann.  
  
 Weitere Informationen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Steuerelemente in Dokumenten  
 Sie können Word\-Dokumenten und Excel\-Arbeitsblättern viele verschiedene Steuerelemente hinzufügen.  Es kann beispielsweise sein, dass Sie einem Dokument ein Steuerelement für die Datumsauswahl hinzufügen möchten, damit Benutzer Datumsangaben im Standardformat eingeben können, oder dass Sie eine Schaltfläche in ein Arbeitsblatt einfügen möchten, mit dem Daten an eine Datenbank gesendet werden können.  
  
 Wenn Sie Projekte auf Dokumentebene für Excel oder Word entwickeln, können Sie dem Dokument oder der Arbeitsmappe im Projekt zur Entwurfszeit mit dem Visual Studio\-Designer Steuerelemente hinzufügen, oder Sie können Sie können Steuerelemente programmgesteuert zur Laufzeit hinzufügen.  Wenn Sie VSTO\-Add\-In\-Projekte für Excel oder Word entwickeln, können Sie allen geöffneten Dokumenten oder Arbeitsmappen zur Laufzeit programmgesteuert Steuerelemente hinzufügen.  
  
 Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md) und [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Kontextmenüs  
 Ein Kontextmenü wird angezeigt, wenn Sie in einem Dokument oder einem Anwendungsfenster mit der rechten Maustaste klicken.  Sie können festlegen, dass nach dem Eintreten eines Ereignisses ein Kontextmenü angezeigt wird, z. B. nach dem Rechtsklick eines Benutzers auf ein Dokument, eine Arbeitsmappe oder ein Hoststeuerelement.  Sie können einem Kontextmenü verschiedene andere Menübefehle oder Steuerelemente hinzufügen.  Erstellen von Kontextmenüs mithilfe von XML  Wenn Sie dem Office\-Projekt ein **Menüband \(XML\)**\-Element hinzufügen, können Sie der Menüband\-XML\-Datei XML\-Code hinzufügen, um Kontextmenüs zu erstellen.  Weitere Informationen zur Verwendung von XML zum Erstellen von Kontextmenüs finden Sie unter [Gewusst wie: Hinzufügen von Befehlen zu Kontextmenüs](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Verwenden von WPF-Steuerelementen in Office-Projektmappen](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Gewusst wie: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  