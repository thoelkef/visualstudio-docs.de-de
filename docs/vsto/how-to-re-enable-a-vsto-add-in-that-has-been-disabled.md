---
title: 'Vorgehensweise: Reaktivieren Sie ein VSTO-Add-in, das deaktiviert wurde'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dfc5a70e309ffece432a2d9c9adb10011557239d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869251"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Vorgehensweise: Reaktivieren Sie ein VSTO-Add-in, das deaktiviert wurde
  VSTO-Add-Ins, die ein unerwartetes Verhalten aufweisen, können von Microsoft Office-Anwendungen deaktiviert werden. Wenn Ihr VSTO-Add-In beim Debuggen von der Anwendung nicht geladen wird, wurde das VSTO-Add-In von der Anwendung möglicherweise hart oder weich deaktiviert.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Hart deaktivierte VSTO-Add-ins  
 Harte Deaktivierung kann auftreten, wenn ein VSTO-Add-in zur unerwarteten Beendigung der Anwendung bewirkt. Sie kann auch auf dem Entwicklungscomputer auftreten, wenn Sie den Debugger beenden, während der <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler im VSTO-Add-In ausgeführt wird.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>So aktivieren Sie ein VSTO-Add-In erneut  
  
1.  Klicken Sie in der Anwendung auf Registerkarte **Datei** .  
  
2.  Klicken Sie auf die Schaltfläche *ApplicationName* **-Optionen** .  
  
3.  Klicken Sie im Bereich "Kategorien" auf **Add-Ins**.  
  
4.  Überprüfen Sie im Detailbereich, ob das VSTO-Add-In in der Liste **Deaktivierte Anwendungs-Add-Ins** angezeigt wird.  
  
     In der Spalte **Name** ist der Name der Assembly und in der Spalte **Speicherort** der vollständige Pfad des Anwendungsmanifests angegeben.  
  
5.  Klicken Sie im Feld **Verwalten** auf **Deaktivierte Elemente**, und klicken Sie dann auf **Gehe zu**.  
  
6.  Wählen Sie das VSTO-Add-In aus, und klicken Sie auf **Aktivieren**.  
  
7.  Klicken Sie auf **Schließen**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Weich deaktivierte VSTO-Add-ins  
 Die weiche Deaktivierung kann auftreten, wenn ein VSTO-Add-In einen Fehler erzeugt, der nicht zur unerwarteten Beendigung der Anwendung führt. Ein VSTO-Add-In kann von einer Anwendung z. B. weich deaktiviert werden, wenn es einen Ausnahmefehler auslöst, während der <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler ausgeführt wird.  
  
> [!NOTE]  
>  Beim erneuten Aktivieren eines weich deaktivierten VSTO-Add-Ins versucht die Anwendung sofort, das VSTO-Add-In zu laden. Wenn das Problem, das anfänglich zur weichen Deaktivierung des VSTO-Add-Ins durch die Anwendung geführt hat, nicht behoben wurde, wird das VSTO-Add-In von der Anwendung erneut weich deaktiviert.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>So aktivieren Sie ein VSTO-Add-In erneut  
  
1.  Klicken Sie in der Anwendung auf Registerkarte **Datei** .  
  
2.  Klicken Sie auf die Schaltfläche *ApplicationName* **-Optionen** .  
  
3.  Klicken Sie im Bereich "Kategorien" auf **Add-Ins**.  
  
4.  Überprüfen Sie im Detailbereich, ob das VSTO-Add-In in der Liste **Inaktive Anwendungs-Add-Ins** angezeigt wird.  
  
     In der Spalte **Name** ist der Name der Assembly und in der Spalte **Speicherort** der vollständige Pfad des Anwendungsmanifests angegeben.  
  
5.  Klicken Sie im Feld **Verwalten** auf **COM-Add-Ins**, und klicken Sie dann auf **Gehe zu**.  
  
6.  Aktivieren Sie im Dialogfeld **COM-Add-Ins** das Kontrollkästchen neben dem deaktivierten VSTO-Add-In.  
  
7.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Debuggen von Office-Projekten](../vsto/debugging-office-projects.md)   
 [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)  
