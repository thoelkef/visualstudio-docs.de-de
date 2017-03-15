---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
In diesem Thema sind allgemeine Probleme aufgelistet, die bei der Arbeit mit [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]\- oder [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]\-Verweisen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auftreten können.  
  
## Fehler beim Zurückgeben von Daten von einem Dienst  
 Wenn ein `DataSet` oder eine `DataTable` von einem Dienst zurückgegeben wird, erhalten Sie möglicherweise den Ausnahmefehler "Die maximale Kontingentgröße für eingehende Nachrichten wurde überschritten".  Die `MaxReceivedMessageSize`\-Eigenschaft für einige Bindungen ist standardmäßig auf einen verhältnismäßig kleinen Wert festgelegt, um die Gefahr von Denial\-of\-Service\-Angriffen zu verringern.  Sie können diesen Wert erhöhen, um den Ausnahmefehler zu verhindern.  Weitere Informationen finden Sie unter <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>.  
  
 So beheben Sie diesen Fehler:  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf die Datei app.config, um sie zu öffnen.  
  
2.  Suchen Sie die `MaxReceivedMessageSize`\-Eigenschaft und erhöhen Sie deren Wert.  
  
## Ein Dienst in Meine Projektmappe kann nicht gefunden werden  
 Wenn Sie im Dialogfeld **Dienstverweis hinzufügen** auf die Schaltfläche **Ermitteln** klicken, werden ein oder mehrere WCF\-Dienstbibliotheksprojekte der Projektmappe nicht in der Diensteliste angezeigt.  Dies kann passieren, wenn der Projektmappe eine noch nicht kompilierte Dienstbibliothek hinzugefügt wurde.  
  
 So beheben Sie diesen Fehler:  
  
-   Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das WCF\-Dienstbibliotheksprojekt, und klicken Sie dann auf **Erstellen**.  
  
## Fehler beim Zugriff auf einen Dienst über einen Remotedesktop  
 Wenn ein Benutzer über eine Remotedesktopverbindung auf einen im Web gehosteten WCF\-Dienst ohne Administratorberechtigungen zugreift, wird die NTLM\-Authentifizierung verwendet.  Wenn der Benutzer nicht über Administratorberechtigungen verfügt, erhält er möglicherweise die folgende Fehlermeldung: "Die HTTP\-Anforderung ist für das Clientauthentifizierungsschema 'Anonym' nicht autorisiert.  Der vom Server empfangene Authentifizierungsheader lautet 'NTLM'."  
  
 So beheben Sie diesen Fehler:  
  
1.  Öffnen Sie im Websiteprojekt die Seite **Eigenschaften**.  
  
2.  Deaktivieren Sie auf der Registerkarte **Startoptionen** das Kontrollkästchen **NTLM\-Authentifizierung**.  
  
    > [!NOTE]
    >  Sie sollten NTLM\-Authentifizierung nur für Websites ausschalten, die ausschließlich WCF\-Dienste enthalten.  Die Sicherheit für WCF\-Dienste wird durch die Konfiguration in der Datei web.config verwaltet.  Dies macht NTLM\-Authentifizierung unnötig.  
  
 Weitere Informationen finden Sie unter [Problembehandlung bei Ausnahmen: System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md).  
  
## Zugriffsebene für Generierte Klassen\-Einstellung hat keine Auswirkungen  
 Das Festlegen der Option **Zugriffsebene für generierte Klassen** im Dialogfeld **Dienstverweis konfigurieren** auf **Intern** oder **Friend** funktioniert unter Umständen nicht.  Obwohl die Option im Dialogfeld festgelegt zu sein scheint, werden in diesem Fall die resultierenden Unterstützungsklassen mit der Zugriffsebene `Public` erstellt.  
  
 Dies ist eine bekannte Einschränkung bestimmter Typen, wie beispielsweise die die unter Verwendung von <xref:System.Xml.Serialization.XmlSerializer> serialisiert wurden.  
  
## Fehler beim Debuggen von Dienstcode  
 Wenn Sie den Code für einen WCF\-Dienst vom Clientcode aus in Einzelschritten ausführen, wird ggf. ein Fehler aufgrund von fehlenden Symbolen ausgegeben.  Dieser Fehler tritt auf, wenn ein Dienst, der Bestandteil der Projektmappe war, verschoben oder aus der Projektmappe entfernt wurde.  
  
 Wenn Sie einen Verweis auf einen WCF\-Dienst in der aktuellen Projektmappe zum ersten Mal hinzufügen, wird eine explizite Buildabhängigkeit zwischen dem Dienstprojekt und dem Dienstclientprojekt eingefügt.  Hierdurch wird gewährleistet, dass der Client immer auf aktuelle Dienstbinärdateien zugreift, was vor allem in Debugging\-Szenarios wichtig ist, z. B. bei schrittweisen Wechseln von Clientcode zu Dienstcode.  
  
 Wenn das Dienstprojekt aus der Projektmappe entfernt wird, wird diese explizite Buildabhängigkeit ungültig.  Visual Studio kann dann nicht mehr garantieren, dass das Dienstprojekt den Anforderungen entsprechend neu erstellt wird.  
  
 Um diesen Fehler zu beheben, müssen Sie das Dienstprojekt manuell neu erstellen:  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** die Option **Projekte und Projektmappen**, und wählen Sie dann **Allgemein** aus.  
  
3.  Stellen Sie sicher, dass das Kontrollkästchen **Erweiterte Buildkonfigurationen anzeigen** aktiviert ist, und klicken Sie dann auf **OK**.  
  
4.  Laden Sie das WCF\-Dienstprojekt.  Weitere Informationen hierzu finden Sie unter [Gewusst wie: Erstellen von Projektmappen mit mehreren Projekten](http://msdn.microsoft.com/de-de/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).  
  
5.  Legen Sie im Dialogfeld **Konfigurations\-Manager** für **Konfiguration der aktuellen Projektmappe** die Option **Debuggen** fest.  Weitere Informationen hierzu finden Sie unter [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).  
  
6.  Wählen Sie im **Projektmappen\-Explorer** das WCF\-Dienstprojekt aus.  
  
7.  Klicken Sie im Menü **Erstellen** auf **Neu erstellen**, um das WCF\-Dienstprojekt neu zu erstellen.  
  
## WCF Data Services werden nicht im Browser angezeigt  
 Beim Versuch, eine XML\-Darstellung von Daten in einem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] anzuzeigen, interpretiert Internet Explorer die Daten u. U. fälschlicherweise als RSS\-Feed.  Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS\-Feeds deaktiviert ist.  
  
 Um diesen Fehler zu beheben, deaktivieren Sie RSS\-Feeds:  
  
1.  Klicken Sie in Internet Explorer im Menü **Extras** auf **Internetoptionen**.  
  
2.  Klicken Sie auf der Registerkarte **Inhalte** im Abschnitt **Feeds** auf **Einstellungen**.  
  
3.  Deaktivieren Sie im Dialogfeld **Feedeinstellungen** das Kontrollkästchen **Feedleseanzeige einschalten**, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie auf **OK**, um das Dialogfeld **Internetoptionen** zu schließen.  
  
## Siehe auch  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/de-de/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)