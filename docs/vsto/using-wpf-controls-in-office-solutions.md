---
title: "Verwenden von WPF-Steuerelementen in Office-Projektmappen | Microsoft Docs"
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
  - "WPF [Office-Entwicklung in Visual Studio]"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Verwenden von WPF-Steuerelementen in Office-Projektmappen
  Mit den Office\-Entwicklungstools in Visual Studio erstellte Projektmappen sind zwar für das direkte Arbeiten mit Windows Forms\-Steuerelementen ausgelegt, Sie können jedoch auch WPF\-Steuerelemente in den Projektmappen verwenden.  Windows Presentation Foundation \(WPF\) bietet eine Alternative zu Windows Forms für das Entwerfen von Benutzeroberflächen.  WPF bietet mithilfe einer Markupsprache namens XAML \(Extensible Application Markup Language\) neue Techniken zum Integrieren von Benutzeroberflächen, Medien und Dokumenten.  Weitere Informationen finden Sie unter [Einführung in WPF in Visual Studio 2015](http://msdn.microsoft.com/library/582a314e-e23d-4144-b45b-acbbd5579252).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Jedes Benutzeroberflächenelement, das Windows Forms\-Steuerelemente in einer Office\-Projektmappe hosten kann, kann auch WPF\-Steuerelemente hosten.  Dazu zählen folgende Elemente:  
  
-   Dokumente und Arbeitsblätter in Anpassungen auf Dokumentebene  
  
-   Aktionsbereiche in Anpassungen auf Dokumentebene  
  
-   Benutzerdefinierte Aufgabenbereiche in VSTO\-Add\-Ins.  
  
-   Formularbereiche in VSTO\-Add\-Ins für Outlook.  
  
## Hinzufügen von WPF\-Steuerelementen zu Office\-Projekten zur Entwurfszeit  
 Sie können Benutzeroberflächenelementen in Office\-Projektmappen WPF\-Steuerelemente nicht direkt hinzufügen.  Fügen Sie dem Projekt stattdessen ein **Benutzersteuerelement \(WPF\)** hinzu, und verwenden Sie es als Entwurfsoberfläche für WPF\-Steuerelemente.  Fügen Sie dann das WPF\-Benutzersteuerelement einem Benutzeroberflächenelement im Projekt hinzu.  
  
#### So fügen Sie einem Aktionsbereich, einem benutzerdefinierten Aufgabenbereich oder einem Formularbereich WPF\-Steuerelemente hinzu  
  
1.  Öffnen Sie ein Projekt, dem Sie einen benutzerdefinierten Aufgabenbereich, einen Aktionsbereich oder einen Formularbereich hinzufügen möchten.  
  
2.  Fügen Sie dem Projekt ein **Benutzersteuerelement \(WPF\)** hinzu.  
  
3.  Fügen Sie aus der **Toolbox** der Entwurfsoberfläche für WPF\-Benutzersteuerelemente WPF\-Steuerelemente hinzu.  
  
     Wenn der WPF\-Benutzersteuerelement\-Designer geöffnet wird, enthält die **Toolbox** standardmäßig nur WPF\-Steuerelemente.  
  
4.  Erstellen Sie das Projekt.  
  
5.  Fügen Sie dem Projekt einen Aktionsbereich, einen Formularbereich oder einen benutzerdefinierten Aufgabenbereich hinzu:  
  
    -   Fügen Sie für Formularbereiche dem Projekt ein Element für den **Outlook\-Formularbereich** hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Fügen Sie dem Projekt für Aktionsbereiche ein **Aktionsbereich\-Steuerelement** oder ein **Benutzersteuerelement** hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) und [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Fügen Sie dem Projekt für benutzerdefinierte Aufgabenbereiche ein **Benutzersteuerelement** hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Ziehen Sie von der Registerkarte *ProjectName* **WPF\-Benutzersteuerelemente** der **Toolbox** das WPF\-Benutzersteuerelement in den Designer für den Aktionsbereich, den Formularbereich oder den benutzerdefinierten Aufgabenbereich.  
  
     Visual Studio erstellt automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>\-Objekt, das das WPF\-Benutzersteuerelement im Benutzeroberflächenelement hostet.  
  
7.  Erstellen Sie das Projekt neu.  
  
#### So fügen Sie einem Dokument oder einem Arbeitsblatt in einem Projekt auf Dokumentebene WPF\-Steuerelemente hinzu  
  
1.  Öffnen Sie ein Projekt auf Dokumentebene für Word oder Excel.  
  
2.  Fügen Sie dem Projekt ein **Benutzersteuerelement \(WPF\)** hinzu.  
  
3.  Fügen Sie aus der **Toolbox** der Entwurfsoberfläche für WPF\-Benutzersteuerelemente WPF\-Steuerelemente hinzu.  
  
4.  Erstellen Sie das Projekt.  
  
5.  Fügen Sie dem Projekt ein **Benutzersteuerelement** \(d. h. ein Windows Forms\-Benutzersteuerelement\) hinzu.  
  
6.  Öffnen Sie den Designer für das Windows Forms\-Benutzersteuerelement.  
  
7.  Ziehen Sie von der Registerkarte *ProjectName* **WPF\-Benutzersteuerelemente** der **Toolbox** das WPF\-Benutzersteuerelement in den Designer.  
  
     Visual Studio erstellt automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>\-Objekt, das das WPF\-Benutzersteuerelement im Windows Forms\-Benutzersteuerelement hostet.  
  
8.  Schreiben Sie Code, der dem Dokument bzw. der Arbeitsmappe das Windows Forms\-Benutzersteuerelement programmgesteuert hinzufügt.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Sie können das Windows Forms\-Benutzersteuerelement im Designer nicht auf das Dokument bzw. das Arbeitsblatt ziehen.  
  
9. Erstellen Sie das Projekt neu.  
  
## Hosten von WPF\-Steuerelementen mithilfe der ElementHost\-Klasse  
 Visual Studio bietet Funktionen, die Sie beim Verwenden von Windows Forms\-Steuerelementen in Office\-Projektmappen unterstützen, aber es fehlen vergleichbare Funktionen für WPF\-Steuerelemente.  Zur Entwurfszeit können Sie z. B. Dokumenten und Arbeitsblättern Windows Forms\-Steuerelemente hinzufügen, indem Sie Steuerelemente aus der **Toolbox** ziehen. Zur Laufzeit können Sie dazu Hilfsmethoden verwenden.  Diese Tools sind jedoch für WPF\-Steuerelemente nicht verfügbar.  
  
 WPF\-Steuerelemente verwenden die <xref:System.Windows.Forms.Integration.ElementHost>\-Klasse als Integrationsebene zwischen einem Windows Forms\-Steuerelement bzw. \-Formular und den WPF\-Steuerelementen.  Wenn Sie der Projektmappe zur Entwurfszeit WPF\-Steuerelemente hinzufügen, generiert Visual Studio automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>\-Objekt.  
  
## WPF\-Ressourcen  
 Weitere Informationen zu Fragen über Architektur und Entwurf beim Hosten von WPF\-Steuerelementen in Windows Forms\-Steuerelementen und \-Formularen finden Sie in den folgenden Themen:  
  
-   [Eingabearchitektur für die Interoperabilität zwischen Windows Forms und WPF](http://msdn.microsoft.com/library/0eb6f137-f088-4c5e-9e37-f96afd28f235)  
  
-   [Eigenschaftenzuordnung von Windows Forms und WPF](http://msdn.microsoft.com/library/999d8298-9c04-467d-a453-86e41002057d)  
  
-   [Interaktion zwischen WPF und Windows Forms](http://msdn.microsoft.com/library/9e8aa6b6-112c-4579-98d1-c974917df499)  
  
-   [Windows Forms\-Steuerelemente und äquivalente WPF\-Steuerelemente](http://msdn.microsoft.com/library/8a157e6b-8054-46db-a5cf-a78966acc7a1)  
  
 Weitere Informationen über das Hinzufügen von WPF\-Steuerelementen zu Windows Forms\-Steuerelementen und \-Formularen in Visual Studio zur Entwurfszeit finden Sie in den folgenden Themen:  
  
-   [Exemplarische Vorgehensweise: Erstellen neuen WPF-Inhalts in Windows Forms zur Entwurfszeit](http://msdn.microsoft.com/library/2e92d8e8-f0e4-4df7-9f07-2acf35cd798c).  
  
-   [Exemplarische Vorgehensweise: Anordnen von WPF-Inhalt in Windows Forms zur Entwurfszeit](http://msdn.microsoft.com/library/5efb1c53-1484-43d6-aa8a-f4861b99bb8a).  
  
-   [Exemplarische Vorgehensweise: Formatieren von WPF-Inhalt](http://msdn.microsoft.com/library/e574aac7-7ea4-4cdb-8034-bab541f000df)  
  
## Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  