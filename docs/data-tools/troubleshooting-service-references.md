---
title: Problembehandlung bei Dienstverweisen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b57547aa9a5fa3c036a534c85cb55bb1749a421b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-references"></a>Problembehandlung bei Dienstverweisen
Dieses Thema listet häufige Probleme, die auftreten können, bei der Arbeit mit [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] oder [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] -Verweise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="error-returning-data-from-a-service"></a>Fehler beim Zurückgeben von Daten von einem Dienst  
 Wenn Sie zurückkehren, eine `DataSet` oder `DataTable` von einem Dienst möglicherweise eine Ausnahme "Kontingent für die maximale Nachrichtengröße für eingehende Nachrichten wurde überschritten". Wird standardmäßig die `MaxReceivedMessageSize` -Eigenschaft für einige Bindungen auf einen relativ kleinen Wert festgelegt, um die Anfälligkeit für Denial-of-Service-Angriffe zu verringern. Sie können diesen Wert, um die Ausnahme zu verhindern, erhöhen. Weitere Informationen finden Sie unter <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.  
  
 Um diesen Fehler zu beheben:  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Datei "App.config", um ihn zu öffnen.  
  
2.  Suchen Sie die `MaxReceivedMessageSize` Eigenschaft, und ändern Sie ihn in einen größeren Wert.  
  
## <a name="cannot-find-a-service-in-my-solution"></a>Einen Dienst in meiner Lösung wurde nicht gefunden.  
 Beim Klicken auf die **Discover** Schaltfläche der **Dienstverweise hinzufügen** (Dialogfeld), ein oder mehrere WCF-Dienstbibliothek-Projekte in der Projektmappe werden in der Liste der Dienste nicht angezeigt. Dies kann auftreten, wenn eine Dienstbibliothek zur Projektmappe hinzugefügt wurde, aber noch nicht kompiliert.  
  
 Um diesen Fehler zu beheben:  
  
-   In **Projektmappen-Explorer**mit der rechten Maustaste auf den WCF-Dienstbibliotheksprojekt, und klicken Sie auf **erstellen**.  
  
## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Fehler beim Zugriff auf einen Dienst über einen Remotedesktop  
 Wenn ein Benutzer greift auf ein im Internet gehosteten WCF-Dienst über eine Remotedesktopverbindung und der Benutzer verfügt nicht über administrative Berechtigungen, NTLM-Authentifizierung verwendet wird. Wenn der Benutzer nicht über Administratorberechtigungen verfügt, kann der Benutzer empfangen die folgende Fehlermeldung angezeigt: "die HTTP-Anforderung ist mit Client-Authentifizierungsschema"Anonymous"nicht autorisiert. Vom Server empfangene Authentifizierungsheader wurde "NTLM"."  
  
 Um diesen Fehler zu beheben:  
  
1.  Öffnen Sie im Website-Projekt die **Eigenschaften** Seiten.  
  
2.  Auf der **Startoptionen** Registerkarte Deaktivieren der **NTLM-Authentifizierung** Kontrollkästchen.  
  
    > [!NOTE]
    >  Sie sollten die NTLM-Authentifizierung nur für Websites deaktivieren, die ausschließlich WCF-Dienste enthalten. Sicherheit für WCF-Diensten wird durch die Konfiguration in der Datei "Web.config" verwaltet. Dadurch wird die NTLM-Authentifizierung nicht erforderlich.  
  
## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Zugriffsebene für generierte Klassen Einstellung hat keine Auswirkung  
 Festlegen der **Zugriffsebene für generierte Klassen** -Option in der **Dienstverweise konfigurieren** Dialogfelds **intern** oder **"Friend"** funktioniert möglicherweise nicht immer. Obwohl die Option angezeigt wird, klicken Sie im Dialogfeld festgelegt werden, die sich ergebenden Unterstützungsklassen generiert werden mit einer Zugriffsebene `Public`.  
  
 Dies ist eine bekannte Einschränkung bestimmter Typen, z. B. solche mit serialisiert die <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="error-debugging-service-code"></a>Fehler beim Debuggen der Dienstcode  
 Wenn Sie in den Code für einen WCF-Dienst aus dem Clientcode schrittweise, wird möglicherweise einen Fehler im Zusammenhang mit fehlenden Symbole erhalten. Dies kann auftreten, wenn ein Dienst, der Teil der Projektmappe wurde aus der Projektmappe entfernt oder verschoben wurde.  
  
 Wenn Sie zunächst einen Verweis auf einen WCF-Dienst, die Teil der aktuellen Projektmappe ist hinzufügen, wird eine explizite Buildabhängigkeit zwischen dem Dienstprojekt und das Dienst-Client-Projekt hinzugefügt. Dadurch wird sichergestellt, die der Client immer auf dem neuesten Stand Dienstbinärdateien, greift auf die ist besonders wichtig für Debugszenarios beschrieben, wie z. B. aus dem Clientcode Einzelschritt Dienstcode.  
  
 Wenn das Dienstprojekt aus der Projektmappe entfernt wird, wird diese explizite Buildabhängigkeit ungültig. Visual Studio nicht mehr garantieren kann, dass das Dienstprojekt neu erstellt, wird nach Bedarf.  
  
 Um diesen Fehler zu beheben, müssen Sie das Dienstprojekt manuell neu erstellen:  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie **Projekte und Projektmappen**, und wählen Sie dann **allgemeine**.  
  
3.  Stellen Sie sicher, dass die **Erweiterte Buildkonfigurationen anzeigen** Kontrollkästchen ausgewählt ist, und klicken Sie dann auf **OK**.  
  
4.  Laden Sie das Projekt für den WCF-Dienst.  
  
5.  In der **Configuration Manager** (Dialogfeld), legen die **aktive Projektmappenkonfiguration** auf **Debuggen**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).  
  
6.  In **Projektmappen-Explorer**, wählen Sie das Projekt für den WCF-Dienst.  
  
7.  Auf der **erstellen** Menü klicken Sie auf **Rebuild** So erstellen Sie das Projekt für den WCF-Dienst neu.  
  
## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services werden nicht im Browser angezeigt.  
 Wenn es versucht, Anzeigen von Daten in eine XML-Darstellung einer [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer möglicherweise fehlinterpretiert werden die Daten als ein RSS-Feed. Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist.  
  
 Um diesen Fehler zu beheben, deaktivieren Sie RSS-Feeds:  
  
1.  In Internet Explorer auf die **Tools** Menü klicken Sie auf **Internetoptionen**.  
  
2.  Auf der **Content** Registerkarte die **Feeds** auf **Einstellungen**.  
  
3.  In der **Feedeinstellungen** deaktivieren Sie im Dialogfeld die **Feedleseanzeige einschalten** Kontrollkästchen, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie auf **OK** schließen die **Internetoptionen** (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)