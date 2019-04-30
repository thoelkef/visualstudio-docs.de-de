---
title: 'Problembehandlung bei Ausnahmen: System.ServiceModel.Security.MessageSecurityException | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6852b12e8a3cbc902770a2825d12697c12fc1760
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436553"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Problembehandlung bei Ausnahmen: System.ServiceModel.Security.MessageSecurityException
Ein <xref:System.ServiceModel.Security.MessageSecurityException> Ausnahme wird ausgelöst, wenn [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] feststellt, dass eine Nachricht nicht ordnungsgemäß gesichert oder manipuliert wurde. Der Fehler tritt am häufigsten auf, wenn alle folgenden Bedingungen zutreffen:  
  
- Sie verwenden einen WCF-Dienstverweis über eine Remoteverbindung, z. B. eine Remotedesktopverbindung oder Terminal Services, um mit einem WCF-Dienst (.svc) in einem Website- oder Webanwendungsprojekt zu kommunizieren.  
  
- Sie haben keine Administratorberechtigungen auf der Remotewebsite.  
  
- Anforderungen an localhost auf der Remotewebsite werden vom [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server behandelt.  
  
## <a name="associated-tips"></a>Tipps  
 **NTLM-Authentifizierungsprobleme zu beheben, wenn Sie den ASP.Net Development Server verwenden.**  
 Für den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server ist normalerweise Windows NT Challenge/Antwortsicherheit (NTLM) ausgeschaltet, sodass anonymer Zugriff erlaubt ist. Beim Ausführen einer Terminal Services-Sitzung oder bei Verwendung einer Remoteverbindung ist die NTLM-Sicherheit jedoch standardmäßig aktiviert. Wenn NTLM aktiviert ist, werden alle localhost-Anforderungen anhand der Anmeldeinformationen des Benutzers oder Prozesses überprüft, der den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server gestartet hat. Dies verringert Sicherheitsrisiken. Die WCF führt jedoch auch eine eigene Authentifizierung durch und lässt nicht zu, dass WCF-Dienste unter einem anderen Konto als einem Administratorkonto genutzt werden.  
  
 Wenn ein Remotebenutzer die Website unter Verwendung des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Servers ausführt und zusätzlich mit einem Webdienst oder WCF-Dienst arbeitet, können Sie entweder eine benutzerdefinierte Dienstbindung erstellen oder die NTLM-Sicherheit deaktivieren.  
  
> [!IMPORTANT]
> Es wird davon abgeraten, die NTLM-Sicherheit zu deaktivieren, da dadurch ein Sicherheitsrisiko entstehen könnte.  
  
 Wenn eine benutzerdefinierte Dienstbindung erstellt wird, bleibt der Schutz durch die NTLM-Authentifizierung weiterhin bestehen.  
  
 Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Dienstbindung für den WCF-Dienst zu erstellen.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>So erstellen Sie einen benutzerdefinierten Dienst zum Binden des auf dem ASP.NET Development Server gehosteten WCF-Diensts  
  
1. Öffnen Sie die Datei Web.config des WCF-Diensts, der die Ausnahme verursacht.  
  
2. Geben Sie die folgenden Informationen in die Datei Web.config ein.  
  
   ```  
   <bindings>  
     <customBinding>  
       <binding name="Service1Binding">  
         <transactionFlow />  
         <textMessageEncoding />  
         <httpTransport authenticationScheme="Ntlm" />  
       </binding>  
     </customBinding>  
   </bindings>  
   ```  
  
3. Speichern und schließen Sie die Datei Web.config.  
  
4. Ändern Sie im Code für den WCF- oder Webdienst den Endpunktwert wie folgt:  
  
   ```  
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
   ```  
  
    Dadurch wird sichergestellt, dass der Dienst die benutzerdefinierte Bindung verwendet.  
  
5. Fügen Sie in der Webanwendung, die auf den Dienst zugreift, einen Verweis auf den Dienst hinzu. (Fügen Sie dem Dienst im Dialogfeld **Dienstverweis hinzufügen** einen Verweis hinzu, und verfahren Sie dabei wie beim ursprünglichen Dienst, der die Ausnahme generiert hat.)  
  
   Mithilfe der folgenden Schritte können Sie die NTLM-Sicherheit bei Verwendung eines WCF-Dienstverweises deaktivieren.  
  
> [!IMPORTANT]
> Es wird davon abgeraten, die NTLM-Sicherheit zu deaktivieren, da dadurch ein Sicherheitsrisiko entstehen könnte.  
  
#### <a name="to-turn-off-ntlm-security"></a>So deaktivieren Sie die NTLM-Sicherheit  
  
1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Websitenamen, und klicken Sie dann auf **Eigenschaftenseiten**.  
  
2. Wählen Sie **Startoptionen**aus, und deaktivieren Sie dann das Kontrollkästchen **NTLM-Authentifizierung** .  
  
3. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Verwenden des Ausnahmen-Assistenten](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)