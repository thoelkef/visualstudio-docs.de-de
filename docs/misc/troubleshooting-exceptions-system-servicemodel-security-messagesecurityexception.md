---
title: "Problembehandlung bei Ausnahmen: System.ServiceModel.Security.MessageSecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.ServiceModel.Security.MessageSecurityException-Ausnahme"
  - "MessageSecurityException-Ausnahme"
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ServiceModel.Security.MessageSecurityException
Eine <xref:System.ServiceModel.Security.MessageSecurityException>\-Ausnahme wird ausgelöst, wenn [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] feststellt, dass eine Meldung nicht ordnungsgemäß gesichert oder manipuliert wurde. Der Fehler tritt am häufigsten auf, wenn alle folgenden Bedingungen zutreffen:  
  
-   Sie verwenden einen WCF\-Dienstverweis über eine Remoteverbindung, z. B. eine Remotedesktopverbindung oder Terminal Services, um mit einem WCF\-Dienst \(.svc\) in einem Website\- oder Webanwendungsprojekt zu kommunizieren.  
  
-   Sie haben keine Administratorberechtigungen auf der Remotewebsite.  
  
-   Anforderungen an localhost auf der Remotewebsite werden vom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server behandelt.  
  
## Tipps  
 **Beheben Sie NTLM\-Authentifizierungsprobleme beim Verwenden des ASP.NET Development Servers.**  
 Für den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server ist normalerweise Windows NT Challenge\/Antwortsicherheit \(NTLM\) ausgeschaltet, sodass anonymer Zugriff erlaubt ist. Beim Ausführen einer Terminal Services\-Sitzung oder bei Verwendung einer Remoteverbindung ist die NTLM\-Sicherheit jedoch standardmäßig aktiviert. Wenn NTLM aktiviert ist, werden alle localhost\-Anforderungen anhand der Anmeldeinformationen des Benutzers oder Prozesses überprüft, der den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server gestartet hat. Dies verringert Sicherheitsrisiken. Die WCF führt jedoch auch eine eigene Authentifizierung durch und lässt nicht zu, dass WCF\-Dienste unter einem anderen Konto als einem Administratorkonto genutzt werden.  
  
 Wenn ein Remotebenutzer die Website unter Verwendung des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Servers ausführt und zusätzlich mit einem Webdienst oder WCF\-Dienst arbeitet, können Sie entweder eine benutzerdefinierte Dienstbindung erstellen oder die NTLM\-Sicherheit deaktivieren.  
  
> [!IMPORTANT]
>  Es wird davon abgeraten, die NTLM\-Sicherheit zu deaktivieren, da dadurch ein Sicherheitsrisiko entstehen könnte.  
  
 Wenn eine benutzerdefinierte Dienstbindung erstellt wird, bleibt der Schutz durch die NTLM\-Authentifizierung weiterhin bestehen.  
  
 Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Dienstbindung für den WCF\-Dienst zu erstellen.  
  
#### So erstellen Sie einen benutzerdefinierten Dienst zum Binden des auf dem ASP.NET Development Server gehosteten WCF\-Diensts  
  
1.  Öffnen Sie die Datei Web.config des WCF\-Diensts, der die Ausnahme verursacht.  
  
2.  Geben Sie die folgenden Informationen in die Datei Web.config ein.  
  
    ```  
    <bindings> <customBinding> <binding name="Service1Binding"> <transactionFlow /> <textMessageEncoding /> <httpTransport authenticationScheme="Ntlm" /> </binding> </customBinding> </bindings>  
    ```  
  
3.  Speichern und schließen Sie die Datei Web.config.  
  
4.  Ändern Sie im Code für den WCF\- oder Webdienst den Endpunktwert wie folgt:  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     Dadurch wird sichergestellt, dass der Dienst die benutzerdefinierte Bindung verwendet.  
  
5.  Fügen Sie in der Webanwendung, die auf den Dienst zugreift, einen Verweis auf den Dienst hinzu. \(Fügen Sie dem Dienst im Dialogfeld **Dienstverweis hinzufügen** einen Verweis hinzu, und verfahren Sie dabei wie beim ursprünglichen Dienst, der die Ausnahme generiert hat.\)  
  
 Mithilfe der folgenden Schritte können Sie die NTLM\-Sicherheit bei Verwendung eines WCF\-Dienstverweises deaktivieren.  
  
> [!IMPORTANT]
>  Es wird davon abgeraten, die NTLM\-Sicherheit zu deaktivieren, da dadurch ein Sicherheitsrisiko entstehen könnte.  
  
#### So deaktivieren Sie die NTLM\-Sicherheit  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Websitenamen, und klicken Sie dann auf **Eigenschaftenseiten**.  
  
2.  Wählen Sie **Startoptionen** aus, und deaktivieren Sie dann das Kontrollkästchen **NTLM\-Authentifizierung**.  
  
3.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)