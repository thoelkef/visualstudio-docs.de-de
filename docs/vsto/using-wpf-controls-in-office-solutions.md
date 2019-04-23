---
title: Verwenden von WPF-Steuerelemente in Office-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8c447ce6b202fc3ccca65c6725e9eb3e5f13ecf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041529"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Verwenden von WPF-Steuerelemente in Office-Projektmappen

Mit den Office-Entwicklungstools in Visual Studio erstellte Projektmappen sind zwar für das direkte Arbeiten mit Windows Forms-Steuerelementen ausgelegt, Sie können jedoch auch WPF-Steuerelemente in den Projektmappen verwenden. Windows Presentation Foundation (WPF) bietet eine Alternative zu Windows Forms für das Entwerfen von Benutzeroberflächen. WPF bietet mithilfe einer Markupsprache namens XAML (Extensible Application Markup Language) neue Techniken zum Integrieren von Benutzeroberflächen, Medien und Dokumenten. Weitere Informationen finden Sie unter [Übersicht über WPF](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Jedes Benutzeroberflächenelement, das Windows Forms-Steuerelemente in einer Office-Projektmappe hosten kann, kann auch WPF-Steuerelemente hosten. Dazu zählen folgende Elemente:

- Dokumente und Arbeitsblätter in Anpassungen auf Dokumentebene

- Aktionsbereiche in Anpassungen auf Dokumentebene

- Benutzerdefinierte Aufgabenbereiche in VSTO-Add-Ins.

- Formularbereiche in VSTO-Add-Ins für Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Hinzufügen von WPF-Steuerelementen zu Office-Projekten zur Entwurfszeit

Sie können Benutzeroberflächenelementen in Office-Projektmappen WPF-Steuerelemente nicht direkt hinzufügen. Fügen Sie stattdessen eine **Benutzersteuerelement (WPF)** Element zu Ihrem Projekt aus, und es als Entwurfsoberfläche für WPF-Steuerelemente verwenden. Fügen Sie dann das WPF-Benutzersteuerelement einem Benutzeroberflächenelement im Projekt hinzu.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>So fügen Sie einem Aktionsbereich, einem benutzerdefinierten Aufgabenbereich oder einem Formularbereich WPF-Steuerelemente hinzu

1. Öffnen Sie ein Projekt, dem Sie einen benutzerdefinierten Aufgabenbereich, einen Aktionsbereich oder einen Formularbereich hinzufügen möchten.

2. Hinzufügen einer **Benutzersteuerelement (WPF)** Element zu Ihrem Projekt.

3. Von der **Toolbox**, WPF-Steuerelemente auf der Entwurfsoberfläche für WPF-Steuerelement hinzufügen.

     Standardmäßig wird bei der WPF-Benutzersteuerelement-Designer geöffnet ist, wird die **Toolbox** nur WPF-Steuerelemente enthält.

4. Erstellen Sie das Projekt.

5. Fügen Sie dem Projekt einen Aktionsbereich, einen Formularbereich oder einen benutzerdefinierten Aufgabenbereich hinzu:

    - Für die Formularbereiche, Hinzufügen einer **Outlook-Formularbereich** Elements zum Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Für Aktionsbereiche, Hinzufügen einer **Aktionsbereich-Steuerelements** oder **Benutzersteuerelement** Elements zum Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) und [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - Für benutzerdefinierte Aufgabenbereiche, Hinzufügen einer **Benutzersteuerelement** Elements zum Projekt. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen ein benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Von der *ProjectName* **WPF-Benutzersteuerelemente** Registerkarte die **Toolbox**, ziehen Sie das WPF-Benutzersteuerelement in den Designer für der Bereich "Aktionen", den Formularbereich oder den benutzerdefinierten Aufgabenbereich.

     Visual Studio erstellt automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>-Objekt, das das WPF-Benutzersteuerelement im Benutzeroberflächenelement hostet.

7. Erstellen Sie das Projekt neu.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>So fügen Sie einem Dokument oder einem Arbeitsblatt in einem Projekt auf Dokumentebene WPF-Steuerelemente hinzu

1. Öffnen Sie ein Projekt auf Dokumentebene für Word oder Excel.

2. Hinzufügen einer **Benutzersteuerelement (WPF)** Element zu Ihrem Projekt.

3. Von der **Toolbox**, WPF-Steuerelemente auf der Entwurfsoberfläche für WPF-Steuerelement hinzufügen.

4. Erstellen Sie das Projekt.

5. Hinzufügen einer **Benutzersteuerelement** Elements (d. h. ein Windows Forms-Benutzersteuerelement) zum Projekt.

6. Öffnen Sie den Designer für das Windows Forms-Benutzersteuerelement.

7. Von der *ProjectName* **WPF-Benutzersteuerelemente** Registerkarte die **Toolbox**, das WPF-Benutzersteuerelement in den Designer ziehen.

     Visual Studio erstellt automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>-Objekt, das das WPF-Benutzersteuerelement im Windows Forms-Benutzersteuerelement hostet.

8. Schreiben Sie Code, der dem Dokument bzw. der Arbeitsmappe das Windows Forms-Benutzersteuerelement programmgesteuert hinzufügt. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Sie können das Windows Forms-Benutzersteuerelement im Designer nicht auf das Dokument bzw. das Arbeitsblatt ziehen.

9. Erstellen Sie das Projekt neu.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>WPF-Steuerungen mithilfe der ElementHost-Klasse

Visual Studio bietet Funktionen, die Sie beim Verwenden von Windows Forms-Steuerelementen in Office-Projektmappen unterstützen, aber es fehlen vergleichbare Funktionen für WPF-Steuerelemente. Angenommen, Sie können hinzufügen Windows Forms-Steuerelementen zu Dokumenten und Arbeitsblättern zur Entwurfszeit durch Ziehen von Steuerelementen aus der **Toolbox**, oder zur Laufzeit mithilfe von Hilfsmethoden zur Verfügung. Diese Tools sind jedoch für WPF-Steuerelemente nicht verfügbar.

WPF-Steuerelemente verwenden die <xref:System.Windows.Forms.Integration.ElementHost>-Klasse als Integrationsebene zwischen einem Windows Forms-Steuerelement bzw. -Formular und den WPF-Steuerelementen. Wenn Sie der Projektmappe zur Entwurfszeit WPF-Steuerelemente hinzufügen, generiert Visual Studio automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>-Objekt.

## <a name="wpf-resources"></a>WPF-Ressourcen

Weitere Informationen zu Fragen über Architektur und Entwurf beim Hosten von WPF-Steuerelementen in Windows Forms-Steuerelementen und -Formularen finden Sie in den folgenden Themen:

- [Windows Forms und WPF-Interoperabilität Eingabearchitektur für die](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Eigenschaftenzuordnung von Windows Forms und WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF und Windows Forms-Interoperabilität](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Windows Forms-Steuerelemente und entsprechende WPF-Steuerelemente](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Weitere Informationen über das Hinzufügen von WPF-Steuerelementen zu Windows Forms-Steuerelementen und -Formularen in Visual Studio zur Entwurfszeit finden Sie in den folgenden Themen:

- [Exemplarische Vorgehensweise: Erstellen von neuen WPF-Inhalts in Windows Forms zur Entwurfszeit](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Exemplarische Vorgehensweise: Anordnen von WPF-Inhalt in Windows Forms zur Entwurfszeit](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Exemplarische Vorgehensweise: Style-WPF-Inhalt](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Siehe auch

- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)
- [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)
- [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)
- [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Vorgehensweise: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
