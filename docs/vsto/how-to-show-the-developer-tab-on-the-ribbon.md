---
title: 'Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 64a0fb4dbc91ff09bddf037a8ce140f134e41e43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614661"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband
  Für den Zugriff auf die **Developer** Registerkarte auf dem Menüband einer Office-Anwendung, müssen Sie konfigurieren, um die Registerkarte angezeigt werden, da er nicht standardmäßig angezeigt wird. Beispielsweise müssen Sie diese Registerkarte anzeigen, wenn Sie <xref:Microsoft.Office.Tools.Word.GroupContentControl> einer Anpassung auf Dokumentebene für Word hinzufügen möchten.

> [!NOTE]
>  Dieser Leitfaden gilt nur für Office 2010-Anwendungen und neuer. Wenn Sie diese Registerkarte im 2007 Microsoft Office System anzeigen möchten, finden Sie die folgende Version dieses Themas [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

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
- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)
