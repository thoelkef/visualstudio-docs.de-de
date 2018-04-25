---
title: 'Vorgehensweise: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung | Microsoft Docs'
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
ms.openlocfilehash: 388523a15ad4d1d4759287fcc1c8ddf32e7b464f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Gewusst wie: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können automatisch oder programmgesteuert nach Updates suchen. Als Entwickler haben Sie große Flexibilität bei der Angabe, wann und wie die Überprüfung auf Updates ausgeführt werden und gibt an, ob Updates erforderlich sind, in dem die Anwendung auf Updates überprüfen soll.  
  
 Sie können die Anwendung zur Überprüfung des Updates automatisch vor dem Starten der Anwendung oder in festgelegten Intervallen nach dem Starten der Anwendung konfigurieren. Darüber hinaus können Sie die mindestens erforderliche Version festlegen. also wird ein Update installiert, wenn der Benutzer Version niedriger als die erforderliche Version ist.  
  
 Sie können die Anwendung zur Überprüfung auf Updates, die programmgesteuert auf Grundlage eines Ereignisses wie einer benutzeranforderung konfigurieren. Im Verfahren "so programmgesteuert auf Updates überprüfen" in diesem Thema wird gezeigt, wie Sie Code schreiben, verwendet die <xref:System.Deployment.Application.ApplicationDeployment> Klasse zur Überprüfung auf Updates auf Grundlage eines Ereignisses.  
  
 Sie können auch Bereitstellen Ihrer Anwendung von einem Speicherort, und aktualisieren Sie es von einem anderen. Finden Sie im Verfahren "So"geben Sie einen anderen Updatepfad.  
  
 Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Updateverhalten wird verwaltet, der **Anwendungsupdates** (Dialogfeld), verfügbar aus den **veröffentlichen** auf der Seite der **Projekt-Designer.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Nach Updates gesucht werden soll, bevor die Anwendung gestartet wird.  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** (Dialogfeld).  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **sollte die Anwendung auf Updates prüfen** Kontrollkästchen aktiviert ist.  
  
5.  In der **auswählen, wann die Anwendung auf Updates überprüfen soll** Abschnitt **vor dem Start der Anwendung**. Dadurch wird sichergestellt, dass Benutzer, die mit dem Netzwerk verbunden sind, immer die Anwendung mit den neuesten Updates ausführen.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Suchen nach Updates im Hintergrund, nachdem die Anwendung gestartet  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** (Dialogfeld).  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass das Kontrollkästchen **sollte die Anwendung auf Updates prüfen** ausgewählt ist.  
  
5.  In der **auswählen, wann die Anwendung für Updates Abschnitt überprüfen sollten**Option **nach dem Starten der Anwendung**. Die Anwendung wird schneller auf diese Weise gestartet und dann Suchen nach Updates im Hintergrund wird, und nur Benutzer benachrichtigen, wenn ein Update verfügbar ist. Nach Abschluss der Installation werden Updates nicht wirksam, bis die Anwendung neu gestartet wird.  
  
6.  In der **Geben Sie die Häufigkeit der Überprüfung auf Updates** Abschnitt, wählen Sie entweder **überprüfen Sie jedes Mal, wenn die Anwendung ausgeführt wird** (Standard) oder **überprüfen jedes** und geben Sie eine Zahl und ein Zeitintervall.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Mindestens erforderliche Version für die Anwendung angeben  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** (Dialogfeld).  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **sollte die Anwendung auf Updates prüfen** Kontrollkästchen aktiviert ist.  
  
5.  Wählen Sie die **geben die mindestens erforderliche Version für diese Anwendung** Kontrollkästchen und geben Sie dann **wichtigen**, **kleinere**, **erstellen**, und  **Revision** Zahlen für die Anwendung.  
  
### <a name="to-specify-a-different-update-location"></a>Zum Angeben eines Speicherorts anderes update  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** (Dialogfeld).  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **sollte die Anwendung auf Updates prüfen** Kontrollkästchen aktiviert ist.  
  
5.  In der **Updatepfad** Feld, geben Sie den Speicherort für die Aktualisierung mit einem vollqualifizierten URL, unter Verwendung des Formats http://Hostname/ApplicationName, oder ein UNC-Pfad im Format \\\Server\ApplicationName, oder klicken Sie auf die **Durchsuchen** Schaltfläche, um für den Updatespeicherort zu navigieren.  
  
### <a name="to-check-for-updates-programmatically"></a>Programmgesteuert nach Updates suchen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Klicken Sie auf die **Updates** die Schaltfläche, um die **Anwendungsupdates** (Dialogfeld).  
  
4.  In der **Anwendungsupdates** Dialogfeld Feld, stellen Sie sicher, dass die **sollte die Anwendung auf Updates prüfen** Kontrollkästchen ist deaktiviert. (Können Sie wahlweise das Kontrollkästchen zum Prüfen auf Updates programmgesteuert und auch die ClickOnce-Common Language Runtime automatisch nach Updates suchen können.)  
  
5.  In der **Updatepfad** Feld, geben Sie den Speicherort für die Aktualisierung mit einem vollqualifizierten URL, unter Verwendung des Formats http://Hostname/ApplicationName, oder ein UNC-Pfad im Format \\\Server\ApplicationName, oder klicken Sie auf die **Durchsuchen** Schaltfläche, um für den Updatespeicherort zu navigieren. Der Updatespeicherort ist, wo die Anwendung sucht nach einer aktualisierten Version von sich selbst.  
  
6.  Erstellen Sie eine Schaltfläche, Menüelement oder andere Benutzer Schnittstelle-Element in einem Windows Form, die Benutzer auswählen können, nach Updates suchen. Rufen Sie Ereignishandler für dieses Element eine Methode zum Überprüfen und Installieren von Updates. Sie finden ein Beispiel für Visual Basic und Visual C#-Code für eine solche Methode im [Vorgehensweise: Überprüfen Sie für die Anwendung programmgesteuert Updates mithilfe der ClickOnce-Bereitstellung API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Erstellen Sie die Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Anwendung aktualisieren (Dialogfeld)](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Gewusst wie: Programmgesteuertes Suchen nach Anwendungsupdates mit der API für die ClickOnce-Bereitstellung](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)