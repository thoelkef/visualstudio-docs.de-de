---
title: Problembehandlung bei Dienstverweisen
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a99cdc4e8c9a4b7551574c93ad6ccdb8c44479df
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927044"
---
# <a name="troubleshoot-service-references"></a>Problembehandlung bei Dienstverweisen

Dieses Thema enthält allgemeine Probleme, die auftreten können, wenn Sie mit Windows Communication Foundation (WCF) oder WCF Data Services-verweisen in Visual Studio arbeiten.

## <a name="error-returning-data-from-a-service"></a>Fehler beim Zurückgeben von Daten von einem Dienst

Bei der Rückkehr eine `DataSet` oder `DataTable` aus einem Dienst möglicherweise eine Ausnahme "das Kontingent für die maximale Nachrichtengröße für eingehende Nachrichten wurde überschritten". In der Standardeinstellung die `MaxReceivedMessageSize` -Eigenschaft für einige Bindungen auf einen relativ kleinen Wert festgelegt ist, um die Anfälligkeit für Denial-of-Service-Angriffe zu verringern. Sie können diesen Wert, um zu verhindern, dass die Ausnahme erhöhen. Weitere Informationen finden Sie unter <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

So beheben Sie diesen Fehler

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die *"App.config"* zu öffnenden Datei.

2.  Suchen Sie die `MaxReceivedMessageSize` Eigenschaft und ändern Sie ihn in einen größeren Wert.

## <a name="cannot-find-a-service-in-my-solution"></a>Einen Dienst in meiner Lösung wurde nicht gefunden.

Beim Klicken auf die **Discover** Schaltfläche der **Hinzufügen von Dienstverweisen** im Dialogfeld eine oder mehrere WCF-Dienstbibliothek-Projekte in der Projektmappe werden in der Liste der Dienste nicht angezeigt. Dies kann auftreten, wenn einer Dienstbibliothek zur Projektmappe hinzugefügt wurde, aber noch nicht kompiliert wurden.

So beheben Sie diesen Fehler

-   In **Projektmappen-Explorer**mit der rechten Maustaste auf das WCF-Dienstbibliothek-Projekt, und klicken Sie auf **erstellen**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Fehler beim Zugriff auf einen Dienst über einen Remotedesktop

Wenn ein Benutzer greift auf eine Web-gehosteten WCF-Diensts über eine Remotedesktopverbindung und der Benutzer verfügt nicht über die administrative Berechtigungen, wird NTLM-Authentifizierung verwendet. Wenn der Benutzer nicht über administrative Berechtigungen verfügt, kann der Benutzer erhalten die folgende Fehlermeldung angezeigt: "die HTTP-Anforderung ist mit dem Clientauthentifizierungsschema"Anonym"nicht autorisiert. Der Authentifizierungsheader, die vom Server empfangen wurde "NTLM"."

So beheben Sie diesen Fehler

1.  Öffnen Sie im Websiteprojekt die **Eigenschaften** Seiten.

2.  Auf der **Startoptionen** Registerkarte die **NTLM-Authentifizierung** Kontrollkästchen.

    > [!NOTE]
    > Sie sollten die NTLM-Authentifizierung für Websites nur deaktivieren, die ausschließlich die WCF-Dienste enthalten. Sicherheit für WCF-Diensten wird durch die Konfiguration in verwaltet die *"Web.config"* Datei. Dadurch wird die NTLM-Authentifizierung nicht erforderlich.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Zugriffsebene für generierte Klassen, die Einstellung hat keine Auswirkungen

Festlegen der **Zugriffsebene für generierte Klassen** option die **Dienstverweis** Dialogfeld **intern** oder **Friend** unter Umständen nicht immer möglich. Obwohl die Option angezeigt wird, um das Dialogfeld festgelegt werden, werden die resultierenden Unterstützungsklassen generiert, mit der Zugriffsebene des `Public`.

Dies ist eine bekannte Einschränkung bestimmter Typen, z. B. mit serialisiert die <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Fehler beim Debuggen der Dienstcode

Wenn Sie in den Code für einen WCF-Dienst über den Clientcode ausführen, erhalten Sie einen Fehler im Zusammenhang mit der Symbole fehlen. Dies kann auftreten, wenn ein Dienst, der Teil der Projektmappe wurde verschoben oder aus der Projektmappe entfernt wurde.

Wenn Sie zuerst einen Verweis auf einen WCF-Dienst, die Teil der aktuellen Projektmappe ist hinzufügen, wird eine explizite Buildabhängigkeit zwischen dem Dienst und das Dienst-Client-Projekt hinzugefügt. Dadurch wird sichergestellt, dass der Client immer auf dem neuesten Stand Dienstbinärdateien zugreift, dies ist besonders wichtig für das Debuggen von Szenarios wie z. B. das schrittweise aus Clientcode Dienstcode.

Wenn das Dienstprojekt aus der Projektmappe entfernt wird, wird diese explizite Buildabhängigkeit ungültig. Visual Studio nicht mehr sicherstellen kann, dass das Service-Projekt neu erstellt, wird nach Bedarf.

Um diesen Fehler zu beheben, müssen Sie das Dienstprojekt manuell neu zu erstellen:

1.  Klicken Sie im Menü **Extras** auf **Optionen**.

2.  In der **Optionen** Dialogfeld erweitern Sie **Projekte und Projektmappen**, und wählen Sie dann **allgemeine**.

3.  Stellen Sie sicher, dass die **Erweiterte Buildkonfigurationen anzeigen** Kontrollkästchen ausgewählt ist, und klicken Sie dann auf **OK**.

4.  Laden Sie das WCF-Dienstprojekt.

5.  In der **Configuration Manager** (Dialogfeld), legen die **aktive Projektmappenkonfiguration** zu **Debuggen**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).

6.  In **Projektmappen-Explorer**, wählen Sie das WCF-Dienst-Projekt.

7.  Auf der **erstellen** Menü klicken Sie auf **Rebuild** das WCF-Dienst-Projekt neu erstellen.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services werden nicht im Browser angezeigt.

Wenn versucht wird, zeigen Sie eine XML-Darstellung der Daten in einem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer kann die Daten wie ein RSS-Feed interpretiert. Stellen Sie sicher, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist.

Um diesen Fehler zu beheben, deaktivieren Sie RSS-Feeds:

1.  Klicken Sie in Internet Explorer im Menü **Extras** auf **Internetoptionen**.

2.  Auf der **Content** Registerkarte die **Feeds** auf **Einstellungen**.

3.  In der **Feedeinstellungen** Dialogfeld das Kontrollkästchen der **Feedleseanzeige einschalten** , und klicken Sie dann auf **OK**.

4.  Klicken Sie auf **OK**, um das Dialogfeld **Internetoptionen** zu schließen.

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)