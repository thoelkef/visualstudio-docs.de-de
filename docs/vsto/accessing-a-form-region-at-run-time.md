---
title: Zugreifen auf einen Formular Bereich zur Laufzeit
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5dd8818b57a1aa33b70254303150d8f00e36cc02
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255800"
---
# <a name="access-a-form-region-at-run-time"></a>Zugreifen auf einen Formular Bereich zur Laufzeit

|Betrifft|
|----------------|
|Die Informationen in diesem Thema gelten nur für die angegebenen Projekttypen und Versionen von Microsoft Office. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Projekttyp:**<br /><br /> -VSTO-Add-in-Projekte<br /><br /> **Microsoft Office-Version**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Verwenden Sie die `Globals` -Klasse, um überall im Outlook-Projekt auf Formularbereiche zuzugreifen. Weitere Informationen `Globals` zur-Klasse finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Zugriffs Formular Bereiche, die in einem bestimmten Outlook-Inspektor-Fenster angezeigt werden
 Um auf alle Formularbereiche in einem bestimmten Inspektor-Fenster zuzugreifen, rufen Sie die `FormRegions` -Eigenschaft der `Globals` -Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt, das den Inspektor darstellt.

 Im folgenden Beispiel wird die Auflistung von Formularbereichen abgerufen, die in dem Inspektor angezeigt werden, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf einen Formularbereich in der Auflistung mit dem Namen `formRegion1` zugegriffen, und der Text, der in einem Textfeld angezeigt wird, wird auf `Hello World`festgelegt.

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Zugriffs Formular Bereiche, die in einem bestimmten Outlook-Explorer-Fenster angezeigt werden
 Um auf alle Formularbereiche in einem bestimmten Explorer-Fenster zuzugreifen, rufen Sie die `FormRegions` -Eigenschaft der `Globals` -Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt, das den Explorer darstellt.

 Im folgenden Beispiel wird die Auflistung von Formularbereichen abgerufen, die in dem Explorer angezeigt werden, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf einen Formularbereich in der Auflistung mit dem Namen `formRegion1` zugegriffen, und der Text, der in einem Textfeld angezeigt wird, wird auf `Hello World`festgelegt.

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>Zugriff auf alle Formular Bereiche
 Um auf alle Formularbereiche zuzugreifen, die in allen Explorern und Inspektoren angezeigt werden, rufen Sie die `FormRegions` -Eigenschaft der `Globals` -Klasse auf.

 Im folgenden Beispiel wird die Auflistung von Formularbereichen abgerufen, die in allen Explorern und Inspektoren angezeigt werden. In diesem Beispiel wird dann auf einen Formularbereich mit dem Namen `formRegion1` zugegriffen, und der Text, der in einem Textfeld angezeigt wird, wird auf `Hello World`festgelegt.

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>Zugreifen auf Steuerelemente in einem Formular Bereich
 Für den Zugriff auf Steuerelemente in einem Formularbereich mithilfe der `Globals` -Klasse müssen Sie die Steuerelemente für Code außerhalb der Formularbereich-Codedatei zugänglich machen.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Im Formular Bereich-Designer entworfene Formular Bereiche
 Ändern Sie für C# den Modifizierer für jedes Steuerelement, auf das Sie zugreifen möchten. Zu diesem Zweck wählen Sie jedes Steuerelement im Formularbereich-Designer aus und ändern im Fenster **Eigenschaften** die **Modifiers** -Eigenschaft in **Internal** oder **public** . Wenn Sie die **Modifier** -Eigenschaft von `textBox1` beispielsweise in **Internal**ändern, können Sie durch Eingabe von `textBox1` auf `Globals.FormRegions.FormRegion1.textBox1`zugreifen.

 Für Visual Basic müssen Sie den Modifizierer nicht ändern.

### <a name="imported-form-regions"></a>Importierte Formular Bereiche
 Beim Importieren eines Formularbereichs, der in Outlook entworfen wurde, wird der Zugriffsmodifizierer jedes Steuerelements im Formularbereich privat. Da der Formularbereich-Designer nicht zum Ändern eines importierten Formularbereichs verwendet werden kann, besteht keine Möglichkeit, den Modifizierer eines Steuerelements im Fenster **Eigenschaften** zu ändern.

 Um den Zugriff auf ein Steuerelement von außerhalb der Formularbereich-Codedatei zu ermöglichen, erstellen Sie in der Formularbereich-Codedatei eine Eigenschaft, um dieses Steuerelement zurückzugeben.

 Weitere Informationen zum Erstellen von Eigenschaften in C#finden [Sie unter Gewusst wie: Deklarieren und Verwenden von Lese &#40;-&#35; /Schreibeigenschaften C-Programmier Handbuch&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties)

 Weitere Informationen zum Erstellen von Eigenschaften in Visual Basic finden [Sie unter Gewusst wie: Erstellen Sie eine Eigenschaft (Visual Basic](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property)).

## <a name="see-also"></a>Siehe auch
- [Richtlinien zum Erstellen von Outlook-Formular Bereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Vorgehensweise: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Benutzerdefinierte Aktionen in Outlook-Formular Bereichen](../vsto/custom-actions-in-outlook-form-regions.md)
- [Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Vorgehensweise: Verhindern, dass Outlook einen Formular Bereich anzeigt](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
