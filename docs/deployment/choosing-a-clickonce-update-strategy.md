---
title: Auswählen einer Strategie für die ClickOnce-Aktualisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4da8dddc667b032c6c284dc62197ff05a1a328f
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081796"
---
# <a name="choose-a-clickonce-update-strategy"></a>Auswählen einer Strategie für ClickOnce-Aktualisierung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann automatische Anwendungsupdates bereitstellen. Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung liest in regelmäßigen Abständen die Bereitstellungsmanifestdatei, um festzustellen, ob Updates für die Anwendung verfügbar sind. Falls verfügbar, wird die neue Version der Anwendung heruntergeladen und ausgeführt. Aus Leistungsgründen werden nur die Dateien heruntergeladen, die sich geändert haben.  
  
 Beim Entwerfen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung müssen Sie bestimmen, welche Strategie die Anwendung bei der Suche nach verfügbaren Updates verfolgen soll. Es gibt drei grundlegende Strategien: Suchen nach Updates beim Anwendungsstart, Suchen nach Updates nach dem Anwendungsstart (in einem Thread im Hintergrund) oder Bereitstellen einer Benutzeroberfläche für Updates.  
  
 Außerdem können Sie bestimmen, wie oft die Anwendung nach Updates suchen soll, und Sie können Updates als obligatorisch kennzeichnen.  
  
> [!NOTE]
>  Für Anwendungsupdates ist eine Netzwerkverbindung erforderlich. Wenn keine Netzwerkverbindung vorhanden ist, wird die Anwendung unabhängig von der ausgewählten Updatestrategie ausgeführt, ohne nach Updates zu suchen.  
  
> [!NOTE]
>  In .NET Framework 2.0 und .NET Framework 3.0, jedes Mal, wenn Ihre Anwendung Überprüfungen für Updates, vor oder nach dem Start oder mithilfe der \<XRef: System.Deployment.Application >-APIs, die Sie festlegen müssen `deploymentProvider` im Bereitstellungsmanifest. Die `deploymentProvider` Element entspricht, in Visual Studio, um die **Updatepfad** Feld der **Updates** im Dialogfeld die **veröffentlichen** Registerkarte. Diese Regel wird in .NET Framework 3.5 gelockert. Weitere Informationen finden Sie unter [Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).  
  
## <a name="check-for-updates-after-application-startup"></a>Nach dem Start der Anwendung nach Updates suchen  
 Bei dieser Strategie versucht die Anwendung während der Ausführung, die Datei mit dem Bereitstellungsmanifest im Hintergrund aufzufinden und zu lesen. Wenn ein Update verfügbar ist, wird der Benutzer beim nächsten Ausführen der Anwendung aufgefordert, das Update zu herunterladen und zu installieren.  
  
 Diese Strategie funktioniert am besten bei Netzwerkverbindungen mit niedriger Bandbreite oder größeren Anwendungen, die lange Downloads erfordern könnten.  
  
 Um diese Updatestrategie zu aktivieren, klicken Sie auf **nach dem Starten der Anwendung** in die **auswählen, wann die Anwendung nach Updates suchen soll** Teil der **Anwendungsupdates** Das Dialogfeld. Geben Sie ein Intervall zum Aktualisieren klicken Sie dann im Abschnitt **angeben, wie häufig die Anwendung nach Updates suchen soll**.  
  
 Dies ist dasselbe wie das Ändern der **Update** -Elements im Anwendungsmanifest wie folgt:  
  
```xml  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="check-for-updates-before-application-startup"></a>Vor dem Start der Anwendung auf Updates prüfen  
 Bei der Standardstrategie wird versucht, die Datei mit dem Bereitstellungsmanifest vor dem Starten der Anwendung aufzufinden und zu lesen. Bei dieser Strategie versucht die Anwendung jedes Mal, wenn der Benutzer die Anwendung startet, die Datei mit dem Bereitstellungsmanifest aufzufinden und zu lesen. Wenn ein Update verfügbar ist, wird es heruntergeladen und gestartet. Andernfalls wird die vorhandene Version der Anwendung gestartet.  
  
 Diese Strategie funktioniert am besten bei Netzwerkverbindungen mit hoher Bandbreite. Bei Verbindungen mit niedriger Bandbreite ist die Verzögerung beim Anwendungsstart möglicherweise nicht akzeptabel.  
  
 Um diese Updatestrategie zu aktivieren, klicken Sie auf **vor dem Start der Anwendung** in die **auswählen, wann die Anwendung nach Updates suchen soll** Teil der **Anwendungsupdates** Das Dialogfeld.  
  
 Dies ist dasselbe wie das Ändern der **Update** -Elements im Anwendungsmanifest wie folgt:  
  
```xml  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="make-updates-required"></a>Kennzeichnen Sie Updates als obligatorisch  
 In bestimmten Situationen ist es erforderlich, dass die Benutzer ausschließlich eine aktualisierte Version der Anwendung ausführen. Angenommen, Sie nehmen eine Änderung an einer externen Ressource vor, z. B. an einem Webdienst, aufgrund derer die ältere Version der Anwendung nicht mehr ordnungsgemäß funktioniert. In dieser Situation würden Sie das Update als obligatorisch kennzeichnen und damit verhindern, dass Benutzer die ältere Version ausführen.  
  
> [!NOTE]
>  Obwohl Sie mit den anderen Updatestrategien Updates erfordern können, überprüfen **vor dem Start der Anwendung** ist die einzige Möglichkeit, um sicherzustellen, dass eine ältere Version nicht ausgeführt werden kann. Wenn das obligatorische Update beim Start ermittelt wird, muss der Benutzer entweder das Update akzeptieren oder die Anwendung schließen.  
  
 Markieren Sie ein Update als erforderlich ist, klicken Sie auf **geben eine mindestens erforderliche Version für diese Anwendung** in die **Anwendungsupdates** Dialogfeld ein, und geben Sie dann die Veröffentlichungsversion (**Hauptversion**, **Kleinere**, **erstellen**, **Revision**), der angibt, dass der niedrigsten Versionsnummer der Anwendung, die installiert werden kann.  
  
 Dies ist identisch mit dem Festlegen der **MinimumRequiredVersion** Attribut der **Bereitstellung** Element im Bereitstellungsmanifest, z. B.:  
  
```xml  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specify-update-intervals"></a>Angeben von Updateintervallen  
 Sie können auch angeben, wie oft die Anwendung nach Updates sucht. Geben Sie dazu an, dass die Anwendung nach dem Starten nach Updates suchen soll, wie zuvor in "Suchen nach Updates nach dem Anwendungsstart" beschrieben.  
  
 Um das Updateintervall anzugeben, legen die **angeben, wie häufig die Anwendung nach Updates suchen soll** Eigenschaften in der **Anwendungsupdates** Dialogfeld.  
  
 Dies ist identisch mit dem Festlegen der **MaximumAge** und **Einheit** Attribute der **Update** -Elements im Bereitstellungsmanifest.  
  
 So können Sie beispielsweise angeben, dass die Anwendung bei jedem Ausführen, einmal die Woche oder einmal im Monat eine Überprüfung durchführt. Wenn zum angegebenen Zeitpunkt keine Netzwerkverbindung vorhanden ist, wird die Suche nach Updates beim nächsten Ausführen der Anwendung durchgeführt.  
  
## <a name="provide-a-user-interface-for-updates"></a>Geben Sie eine Benutzeroberfläche für updates  
 Bei dieser Strategie stellt der Anwendungsentwickler eine Benutzeroberfläche bereit, in der Benutzer auswählen können, wann und wie oft die Anwendung nach Updates sucht. So können Sie z. B. ein Menüelement "Jetzt auf Updates überprüfen" oder ein Dialogfeld "Updateeinstellungen" mit Auswahlmöglichkeiten für unterschiedliche Updateintervalle bereitstellen. Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellungs-APIs bieten ein Framework zum Programmieren Ihrer eigenen Benutzeroberfläche aktualisieren. Weitere Informationen finden Sie unter den Ausführungen zum <xref:System.Deployment.Application>-Namespace.  
  
 Wenn eine Anwendung Bereitstellungs-APIs zur Steuerung einer eigenen Updatelogik verwendet, sollten Sie die Suche nach Updates blockieren, wie im folgenden Abschnitt unter "Verhindern der Suche nach Updates" beschrieben.  
  
 Diese Strategie funktioniert am besten, wenn Sie unterschiedliche Updatestrategien für unterschiedliche Benutzer vorsehen möchten.  
  
## <a name="block-update-checking"></a>Blockieren Sie die Überprüfung der Aktualisierung  
 Sie können die Anwendung auch daran hindern, nach Updates zu suchen. Dies kann beispielsweise der Fall sein, wenn eine einfache Anwendung nie aktualisiert wird, Sie aber die einfache Installation der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellung nutzen möchten.  
  
 Sie sollten auch überprüfen, ob Ihre Anwendung bereitstellungs-APIs verwendet, um die eigenen Aktualisierungen Update blockieren; finden Sie unter "eine Benutzeroberfläche für Updates weiter oben in diesem Thema sind".  
  
 Deaktivieren Sie zur Überprüfung der Aktualisierung zu blockieren, die **die Anwendung soll nach Updates suchen** Kontrollkästchen im Dialogfeld für die Updates der Anwendung.  
  
 Sie können die Suche nach Updates auch verhindern, indem Sie das `<Subscription>`-Tag aus dem Bereitstellungsmanifest entfernen.  
  
## <a name="permission-elevation-and-updates"></a>Berechtigungserweiterung und updates  
 Wenn eine neue Version einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung für die Ausführung eine höhere Vertrauensebene als die vorherige Version erfordert, wird der Benutzer durch [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in einer Eingabeaufforderung gefragt, ob die Anwendung diese höhere Vertrauensebene erhalten soll. Wenn der Benutzer das Gewähren der höheren Vertrauensebene ablehnt, wird das Update nicht installiert. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fordert den Benutzer beim nächsten Starten auf, die Anwendung wieder zu installieren. Wenn der Benutzer zu diesem Zeitpunkt die höhere Vertrauensebene nicht gewährt und das Update nicht als erforderlich gekennzeichnet ist, wird die alte Version der Anwendung ausgeführt. Ist das Update jedoch erforderlich, wird die Anwendung erst wieder ausgeführt, wenn der Benutzer die höhere Vertrauensebene akzeptiert.  
  
 Wenn Sie die Bereitstellung vertrauenswürdiger Anwendungen verwenden, wird keine Eingabeaufforderung für Vertrauensebenen angezeigt. Weitere Informationen finden Sie unter [Übersicht über die Bereitstellung von vertrauenswürdigen Anwendung](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Siehe auch  
 \<XRef: System.Deployment.Application >   
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Wählen Sie eine Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Wie ClickOnce Anwendungsupdates ausführt](../deployment/how-clickonce-performs-application-updates.md)   
 [Gewusst wie: Verwalten von Updates für eine ClickOnce-Anwendung](../deployment/how-to-manage-updates-for-a-clickonce-application.md)