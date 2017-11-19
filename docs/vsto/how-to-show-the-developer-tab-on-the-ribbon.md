---
title: "Vorgehensweise: Anzeigen der Registerkarte \"Entwickler\" im Menüband | Microsoft Docs"
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
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cad7fb4fe49df9688a0b9e7b3baa1f1108694136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste
  Für den Zugriff auf die **Developer** Registerkarte auf dem Menüband einer Office-Anwendung, müssen Sie konfigurieren, um die Registerkarte angezeigt werden, weil es nicht standardmäßig angezeigt wird. Beispielsweise müssen Sie diese Registerkarte anzeigen, wenn Sie <xref:Microsoft.Office.Tools.Word.GroupContentControl> einer Anpassung auf Dokumentebene für Word hinzufügen möchten.  
  
> [!NOTE]  
>  Dieser Leitfaden gilt nur für Office 2010-Anwendungen und neuer. Wenn Sie diese Registerkarte im 2007 Microsoft Office System anzeigen möchten, finden Sie die folgende Version dieses Themas [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" im Menüband](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Access enthält keine **Developer** Registerkarte.  
  
### <a name="to-show-the-developer-tab"></a>Anzeigen der Registerkarte "Entwickler"  
  
1.  Starten Sie eine der Office-Anwendungen, die in diesem Thema beschrieben werden. Finden Sie unter der **gilt für:** Hinweis weiter oben in diesem Thema.  
  
2.  Auf der **Datei** Registerkarte, und wählen Sie die **Optionen** Schaltfläche.  
  
     Die folgende Abbildung zeigt die **Datei** Registerkarte und **Optionen** Schaltfläche in Office 2010.  
  
     ![Wählen Sie die Datei, in Outlook 2010 Optionen](../vsto/media/vsto-office-file-tab.png "wählen Sie die Datei, in Outlook 2010-Optionen")  
  
     Die folgende Abbildung zeigt die **Datei** Registerkarte in Office 2013.  
  
     ![Die Registerkarte "Datei" in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Registerkarte "der Datei" in Outlook 2013")  
  
     Die folgende Abbildung zeigt die **Optionen** Schaltfläche in Office 2013.  
  
     ![Die Schaltfläche "Optionen" in Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Options-Schaltfläche in Outlook 2013 Preview")  
  
3.  In der *Parameter "ApplicationName"***Optionen** Dialogfeld Wählen Sie die **Menüband anpassen** Schaltfläche.  
  
     Die folgende Abbildung zeigt die **Optionen** Dialogfeld und der **Menüband anpassen** Schaltfläche in Excel 2010. Der Speicherort dieser Schaltfläche ist bei allen anderen Anwendungen vergleichbar, die im Abschnitt "Betrifft" oben in diesem Thema aufgeführt werden.  
  
     ![Die Schaltfläche "Menüband anpassen"](../vsto/media/vsto-office2010-customizeribbonbutton.png "der anpassen Menübandschaltfläche")  
  
4.  Wählen Sie in der Liste der Hauptregisterkarten das **Developer** Kontrollkästchen.  
  
     Die folgende Abbildung zeigt die **Developer** Kontrollkästchen in Word 2010 und [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Der Speicherort dieses Kontrollkästchens ist bei allen anderen Anwendungen vergleichbar, die im Abschnitt "Betrifft" oben in diesem Thema aufgeführt werden.  
  
     ![Klicken Sie im Dialogfeld "Word-Optionen" das Kontrollkästchen Developer](../vsto/media/vsto-office2010-developercheckbox.png "der Developer-Kontrollkästchen, klicken Sie im Dialogfeld "Word-Optionen"")  
  
5.  Wählen Sie die **OK** Schaltfläche zum Schließen der **Optionen** (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)  
  
  