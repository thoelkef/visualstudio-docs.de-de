---
title: "Vorgehensweise: Anpassen der mehrsprachige Benutzeroberfläche von Office | Microsoft Docs"
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
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39ee8b6bdcb4ad647164ec555cfa37ee9cfe8f50
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Gewusst wie: Anpassen an die mehrsprachige Benutzeroberfläche von Office
  Die Multilingual User Interface (MUI) ist eine Microsoft Office-Funktion, die der Endbenutzer die Möglichkeit zum Ändern der Sprache der Benutzeroberfläche (UI) bietet. Ein Endbenutzer mit einer englischen Benutzeroberfläche arbeiten können z. B. die Sprache der Benutzeroberfläche auf Spanisch ändern.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Wenn Ihre Anwendung von Personen, die mehrere Sprachen von Office verwenden verwendet wird, können Sie Code aus, um automatisch ändern der Sprache Ihre UI-Zeichenfolgen entsprechend die Sprache, die von Office auf dem Computer des Benutzers verwendet wird, (wenn der Benutzer die erforderlichen Ressourcen installiert wurde) hinzufügen.  
  
### <a name="to-check-the-current-office-ui-setting"></a>Überprüfen Sie die aktuelle Einstellung für die Office-Benutzeroberfläche  
  
1.  Verwenden der <xref:System.Threading.Thread.CurrentUICulture%2A> Eigenschaft des aktuellen Threads. Festlegen der Sprache der UI-Zeichenfolgen entsprechend die Sprache, die von der Version von Office, die zurzeit ausgeführt wird, auf dem Computer des Benutzers verwendet wird.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Siehe auch  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Spätes Binden in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)  
  
  