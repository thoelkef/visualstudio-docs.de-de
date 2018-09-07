---
title: 'Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf dem Menüband'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fea1b0fa804726cb43bdc5b6d866ceedc186924c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780433"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf dem Menüband
  Für den Zugriff auf die **Developer** Registerkarte auf dem Menüband einer Office-Anwendung, müssen Sie konfigurieren, um die Registerkarte angezeigt werden, da er nicht standardmäßig angezeigt wird. Beispielsweise müssen Sie diese Registerkarte anzeigen, wenn Sie <xref:Microsoft.Office.Tools.Word.GroupContentControl> einer Anpassung auf Dokumentebene für Word hinzufügen möchten.  
  
> [!NOTE]  
>  Dieser Leitfaden gilt nur für Office 2010-Anwendungen und neuer. Wenn Sie diese Registerkarte im 2007 Microsoft Office System anzeigen möchten, finden Sie die folgende Version dieses Themas [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Zugriff verfügt nicht über eine **Developer** Registerkarte.  
  
## <a name="to-show-the-developer-tab"></a>Anzeigen der Registerkarte "Entwickler"  
  
1.  Starten Sie eine der Office-Anwendungen, die in diesem Thema beschrieben werden. Finden Sie unter den **gilt für:** Anmerkung weiter oben in diesem Thema.  
  
2.  Auf der **Datei** Registerkarte die **Optionen** Schaltfläche.  
  
     Die folgende Abbildung zeigt die **Datei** Registerkarte und **Optionen** -Schaltfläche in Office 2010.  
  
     ![Wählen die Datei, "Optionen" in Outlook 2010](../vsto/media/vsto-office-file-tab.png "wählen die Datei, \"Optionen\" in Outlook 2010")  
  
     Die folgende Abbildung zeigt die **Datei** Registerkarte in Office 2013.  
  
     ![Die Registerkarte "Datei" in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "der Datei-Registerkarte in Outlook 2013")  
  
     Die folgende Abbildung zeigt die **Optionen** -Schaltfläche in Office 2013.  
  
     ![Die Schaltfläche "Optionen" in Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "die Optionsschaltfläche in Outlook 2013 Preview")  
  
3.  In der _ApplicationName_**Optionen** Dialogfeld auf die **Menüband anpassen** Schaltfläche.  
  
     Die folgende Abbildung zeigt die **Optionen** Dialogfeld und der **Menüband anpassen** -Schaltfläche in Excel 2010. Der Speicherort dieser Schaltfläche ist bei allen anderen Anwendungen vergleichbar, die im Abschnitt "Betrifft" oben in diesem Thema aufgeführt werden.  
  
     ![Die Schaltfläche "Menüband anpassen"](../vsto/media/vsto-office2010-customizeribbonbutton.png "Schaltfläche \"Menüband anpassen\"")  
  
4.  Wählen Sie in der Liste der Hauptregisterkarten das **Developer** Kontrollkästchen.  
  
     Die folgende Abbildung zeigt die **Developer** Kontrollkästchen in Word 2010 und [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Der Speicherort dieses Kontrollkästchens ist bei allen anderen Anwendungen vergleichbar, die im Abschnitt "Betrifft" oben in diesem Thema aufgeführt werden.  
  
     ![Das Kontrollkästchen "Entwickler" in das Dialogfeld "Word-Optionen"](../vsto/media/vsto-office2010-developercheckbox.png "The Developer-Kontrollkästchen im Dialogfeld \"Word-Optionen\"")  
  
5.  Wählen Sie die **OK** Schaltfläche zum Schließen der **Optionen** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)  
  
  