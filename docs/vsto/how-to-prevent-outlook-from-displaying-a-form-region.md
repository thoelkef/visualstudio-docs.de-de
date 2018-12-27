---
title: 'Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook'
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aaeafe14f35092be30c982ebb758e40afedb8aa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647080"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook
  Es gibt möglicherweise Situationen, in denen Sie nicht über Microsoft Office Outlook einen Formularbereich für ein bestimmtes Element anzeigen möchten. Wenn Sie ein Kontaktelement keine Geschäftsadresse enthält, können Sie beispielsweise einen Formularbereich verhindern, der zeigt den Speicherort des Unternehmens in einer Karte angezeigt werden.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Um zu verhindern, dass Outlook einen Formularbereich anzeigen  
  
1. Öffnen Sie die Codedatei für den Formularbereich ein, die, den Sie ändern möchten.  
  
2. Erweitern Sie die **Formularbereichsfactory** Codebereich.  
  
3. Fügen Sie Code in die `FormRegionInitializing` -Ereignishandler, der festlegt der <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Eigenschaft der <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> -Klasse **"true"**.  
  
   In diesem Beispiel, wenn das Kontaktelement eine Adresse keinen enthält die <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> -Eigenschaftensatz auf **"true"**, und der Formularbereich wird nicht angezeigt.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Exemplarische Vorgehensweise: Importieren Sie einen, der in Outlook entworfenen Formularbereich](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  