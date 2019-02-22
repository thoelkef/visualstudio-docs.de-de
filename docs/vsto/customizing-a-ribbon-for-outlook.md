---
title: Anpassen eines Menübands für Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58735a36afd48132f919e370da5e27fd0c42a0f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614960"
---
# <a name="customize-a-ribbon-for-outlook"></a>Anpassen eines Menübands für Outlook
  Beim Anpassen des Menübands in Microsoft Office Outlook müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird. Outlook zeigt das Menüband in der Benutzeroberfläche der Hauptanwendung und in Fenstern an, die geöffnet werden, wenn Benutzer bestimmte Aufgaben ausführen, z. B. eine E-Mail erstellen. Diese Anwendungsfenster werden als Inspektoren bezeichnet.

 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Verwenden des Menüband-Designers zum Anpassen des Menübands in Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Eine benutzerdefinierte Multifunktionsleiste hinzugefügt, um die Benutzeroberfläche der hauptanwendung
 Die Benutzeroberfläche der Hauptanwendung in Outlook ist der Explorer. Bei Verwendung der **Menüband (visueller Designer)** , Sie können ein Menüband hinzufügen im Explorer durch Klicken auf die **RibbonType** -Eigenschaft des Menübands in die **Eigenschaften** Fenster auswählen und dann **Microsoft.Outlook.Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Ein Menüband eines Inspektors zuweisen
 Sie identifizieren den anzupassenden Inspektor durch Angabe des Menübandtyps, der der Nachrichtenklasse des Inspektors entspricht.

 Bei Verwendung der **Menüband (visueller Designer)** Element, klicken Sie auf die **RibbonType** -Eigenschaft des Menübands in die **Eigenschaften** Fenster, und wählen Sie dann einen oder mehrere Menüband-IDs aus die Liste der Werte.

 Sie können einem Projekt mehrere Menübänder hinzufügen. Wenn sich mehrere Menübänder eine Menüband-ID teilen, überschreiben Sie die `CreateRibbonExtensibilityObject`-Methode in der `ThisAddin`-Klasse des Projekts, um anzugeben, welches Menüband zur Laufzeit angezeigt werden soll. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md). Weitere Informationen zu den einzelnen Menübandtypen, finden Sie im technischen Artikel [Anpassen des Menübands in Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Angeben des Menübandtyps mithilfe des Menüband-XML
 Bei Verwendung der **Menüband (XML)** Element, überprüfen Sie den Wert von der *RibbonID* Parameter in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode, und geben Sie das entsprechende Menüband zurück.

 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>-Methode wird automatisch von Visual Studio in der Menüband-Codedatei generiert. Die *RibbonID* Parameter ist eine Zeichenfolge, die den Explorer oder einen bestimmten Typ von Inspektor angibt. Eine vollständige Liste der möglichen Werte der *RibbonID* Parameter finden Sie im technischen Artikel [Anpassen des Menübands in Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur im `Microsoft.Outlook.Mail.Compose`-Inspektor angezeigt wird. Dies ist der Inspektor, der geöffnet wird, wenn ein Benutzer eine neue E-Mail erstellt. Das anzuzeigende Menüband wird angegeben, der `GetResourceText()` -Methode, die in generiert, wird die **Menüband** Klasse. Weitere Informationen zu den **Menüband** Klasse, finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Siehe auch
- [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Menüband-designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
