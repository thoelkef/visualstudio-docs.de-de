---
title: 'Vorgehensweise: Die mehrsprachige Benutzeroberfläche von Office als Ziel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c495f8a83b58c53404056befd2227b295c3324d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961138"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Vorgehensweise: Die mehrsprachige Benutzeroberfläche von Office als Ziel
  Die Multilingual User Interface (MUI) ist ein Microsoft Office-Feature, das der Endbenutzer die Möglichkeit zum Ändern der Sprache der Benutzeroberfläche (UI) bietet. Beispielsweise kann ein Endbenutzer mit einer englischen Benutzeroberfläche arbeiten die Sprache der Benutzeroberfläche auf Spanisch ändern.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Wenn Ihre Anwendung von Personen, die viele Sprachen von Office verwenden verwendet wird, können Sie Code so ändern Sie automatisch die Sprache des Ihre UI-Zeichenfolgen entsprechend die Sprache, die von Office auf dem Computer des Benutzers verwendet wird, (wenn der Benutzer die richtigen Ressourcen, die installiert hat) hinzufügen.

## <a name="to-check-the-current-office-ui-setting"></a>Überprüfen Sie die aktuelle Einstellung für die Office-Benutzeroberfläche

1. Verwenden der <xref:System.Threading.Thread.CurrentUICulture%2A> Eigenschaft des aktuellen Threads. Legen Sie die Sprache des Ihre UI-Zeichenfolgen entsprechend die Sprache ein, die die Version von Office, die derzeit auf dem Computer des Benutzers ausgeführt wird.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Verweisen Sie auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Spätes Binden in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)
