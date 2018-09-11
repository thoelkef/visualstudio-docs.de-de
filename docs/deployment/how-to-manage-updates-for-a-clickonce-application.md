---
title: 'Vorgehensweise: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd9d8d7e88bc9ee8c8b041571ddaa258067c300
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283651"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Gewusst wie: Verwalten von Updates für eine ClickOnce-Anwendung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können automatisch oder programmgesteuert nach Updates suchen. Als Entwickler müssen Sie große Flexibilität bei der Angabe, wann und wie Updates gesucht werden und gibt an, ob Updates erforderlich sind, in dem die Anwendung nach Updates suchen soll.  
  
 Sie können konfigurieren, dass die Anwendung für Updates automatisch vor dem Start der Anwendung oder in bestimmten Zeitabständen überprüfen, nachdem die Anwendung gestartet. Darüber hinaus können Sie die mindestens erforderliche Version angeben; d. h. ist ein Update installiert, wenn der Benutzer-Version niedriger als die erforderliche Version ist.  
  
 Sie können die Anwendung für die Prüfung auf Updates, die programmgesteuert auf Grundlage eines Ereignisses, z. B. eine benutzeranforderung konfigurieren. Im Verfahren "so programmgesteuert auf Updates überprüfen" in diesem Thema wird gezeigt, wie Sie Code schreiben würden, verwendet der <xref:System.Deployment.Application.ApplicationDeployment> Klasse, um nach Updates suchen auf der Grundlage von Ereignissen.  
  
 Auch können Sie Ihre Anwendung von einem Speicherort bereitstellen und aktualisieren Sie sie von einem anderen. Finden Sie im Verfahren "So"geben Sie einen anderen Updatepfad.  
  
 Weitere Informationen finden Sie unter [Auswählen einer Strategie der ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Updateverhalten wird verwaltet, der **Anwendungsupdates** im Dialogfeld aus der **veröffentlichen** auf der Seite die **Projekt-Designer.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Nach Updates gesucht werden soll, bevor die Anwendung gestartet wird.  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** Dialogfeld.  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **die Anwendung soll nach Updates suchen** das Kontrollkästchen aktiviert ist.  
  
5.  In der **auswählen, wann die Anwendung nach Updates suchen soll** wählen Sie im Abschnitt **vor dem Start der Anwendung**. Dadurch wird sichergestellt, dass Benutzer, die mit dem Netzwerk verbunden sind, immer die Anwendung mit den neuesten Updates ausgeführt werden.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Für die Prüfung auf Updates im Hintergrund, nachdem die Anwendung gestartet  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** Dialogfeld.  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass das Kontrollkästchen **die Anwendung soll nach Updates suchen** ausgewählt ist.  
  
5.  In der **auswählen, wann die Anwendung nach Updates im Abschnitt suchen, sollten**Option **nach dem Starten der Anwendung**. Die Anwendung wird schneller auf diese Weise gestartet, und klicken Sie dann nach Updates suchen im Hintergrund wird, und nur die Benutzer benachrichtigen, wenn ein Update verfügbar ist. Nach Abschluss der Installation werden Updates nicht wirksam, bis die Anwendung neu gestartet wird.  
  
6.  In der **angeben, wie häufig die Anwendung nach Updates suchen soll** Abschnitt, wählen Sie entweder **überprüfen Sie jedes Mal, wenn die Anwendung ausgeführt wird** (Standard) oder **überprüfen jeder** und geben Sie eine Zahl und ein Zeitintervall.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Mindestens erforderliche Version für die Anwendung angeben  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** Dialogfeld.  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **die Anwendung soll nach Updates suchen** das Kontrollkästchen aktiviert ist.  
  
5.  Wählen Sie die **geben eine mindestens erforderliche Version für diese Anwendung** aus, und geben Sie dann **wichtigen**, **kleinere**, **erstellen**, und  **Revision** Zahlen für die Anwendung.  
  
### <a name="to-specify-a-different-update-location"></a>Zum Angeben eines Speicherorts für die anderen Updates  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** Dialogfeld.  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **die Anwendung soll nach Updates suchen** das Kontrollkästchen aktiviert ist.  
  
5.  In der **Updatepfad** Geben Sie den Speicherort für die Aktualisierung mit einer vollqualifizierten URL, die mit dem Format *http://Hostname/ApplicationName*, oder einen UNC-Pfad im Format  *\\\Server\ ApplicationName*, oder klicken Sie auf die **Durchsuchen** Schaltfläche um den Updatepfad suchen.  
  
### <a name="to-check-for-updates-programmatically"></a>Programmgesteuert nach Updates suchen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** Dialogfeld.  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **die Anwendung soll nach Updates suchen** Kontrollkästchen deaktiviert ist. (Optional können Sie auswählen dieses Kontrollkästchen, überprüfen Sie, ob Updates programmgesteuert und auch die ClickOnce-Laufzeit, die automatisch nach Updates suchen können.)  
  
5.  In der **Updatepfad** Geben Sie den Speicherort für die Aktualisierung mit einer vollqualifizierten URL, die mit dem Format *http://Hostname/ApplicationName*, oder einen UNC-Pfad im Format  *\\\Server\ ApplicationName*, oder klicken Sie auf die **Durchsuchen** Schaltfläche um den Updatepfad suchen. Speicherort für die Aktualisierung ist, wo die Anwendung nach einer aktualisierten Version von sich selbst sucht.  
  
6.  Erstellen Sie eine Schaltfläche, Menüelement oder andere Benutzeroberflächenelemente in einem Windows Form, die Benutzer ausgewählt werden, nach Updates suchen. Elements-Ereignishandler rufen Sie eine Methode zum Suchen und installieren Sie Updates aus. Sie finden ein Beispiel für Visual Basic und Visual C#-Code für eine solche Methode im [wie: Suchen nach Anwendungsupdates programmgesteuert mithilfe der API für der ClickOnce-Bereitstellung](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Erstellen Sie Ihre Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Updates (Dialogfeld)](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))   
 [Auswählen einer Strategie für ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Veröffentlichen von ClickOnce-Anwendungslösungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Gewusst wie: Suchen nach Anwendungsupdates programmgesteuert mithilfe der API für der ClickOnce-Bereitstellung](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)