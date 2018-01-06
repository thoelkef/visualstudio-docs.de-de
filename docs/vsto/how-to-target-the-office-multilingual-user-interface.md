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
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3de0e73a4a5a5cf10cd0f378a2d00d3c4da1b2d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
  