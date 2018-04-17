---
title: 'Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5fffde6cd92d490df2a5567763da77e723ed4f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook
  Es gibt möglicherweise Situationen, in denen Sie nicht über Microsoft Office Outlook einen Formularbereich für ein bestimmtes Element anzeigen möchten. Wenn ein Kontaktelement keine Geschäftsadresse enthält, können Sie z. B. einen Formularbereich verhindern, der in einer Karte angezeigt wird, den Speicherort des Geschäfts anzeigt.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Um zu verhindern, dass Outlook Anzeige eines Formularbereichs  
  
1.  Öffnen Sie die Codedatei für den Formularbereich, die, den Sie ändern möchten.  
  
2.  Erweitern Sie die **Formularbereichsfactory** Codebereich.  
  
3.  Code Hinzufügen der `FormRegionInitializing` -Ereignishandler, der festlegt der <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Eigenschaft von der <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> Klasse **"true"**.  
  
 In diesem Beispiel, wenn das Kontaktelement eine Adresse keinen enthält die <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> -Eigenschaftensatz auf **"true"**, und die Formularbereich wird nicht angezeigt.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  