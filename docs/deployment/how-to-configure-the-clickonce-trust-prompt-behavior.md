---
title: "How to: Configure the ClickOnce Trust Prompt Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, install without prompting"
  - "deploying applications [ClickOnce], trust prompt"
  - "ClickOnce applications, install without prompting"
  - "ClickOnce applications, trust prompt"
  - "ClickOnce deployment, trust prompt"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Configure the ClickOnce Trust Prompt Behavior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die vertrauenswürdige ClickOnce\-Eingabeaufforderung konfigurieren, um Endbenutzern ggf. das Installieren von ClickOnce\-Anwendungen wie Windows Forms\-Anwendungen, Windows Presentation Foundation\-Anwendungen, Konsolenanwendungen, WPF\-Browseranwendungen und Office\-Projektmappen zu ermöglichen.  Die Konfiguration der vertrauenswürdigen Eingabeaufforderung erfolgt durch Festlegen von Registrierungsschlüsseln auf dem Computer der Endbenutzer.  
  
 In der folgenden Tabelle werden die Konfigurationsoptionen angezeigt, die für jede der fünf Zonen \(Internet, UntrustedSites, MYCOMPUTER, LocalIntranet und TrustedSites\) verwendet werden können.  
  
|Option|Registrierungseinstellung|Beschreibung|  
|------------|-------------------------------|------------------|  
|Vertrauenswürdige Eingabeaufforderung aktivieren|`Aktiviert`|Die vertrauenswürdige ClickOnce\-Eingabeaufforderung wird angezeigt, damit Endbenutzer ClickOnce\-Anwendungen Vertrauenswürdigkeit gewähren können.|  
|Vertrauenswürdige Eingabeaufforderung einschränken|`AuthenticodeRequired`|Die vertrauenswürdige ClickOnce\-Eingabeaufforderung wird nur angezeigt, wenn ClickOnce\-Anwendungen mit einem Zertifikat signiert sind, das den Herausgeber identifiziert.|  
|Vertrauenswürdige Eingabeaufforderung deaktivieren|`Disabled`|Die vertrauenswürdige ClickOnce\-Eingabeaufforderung wird nicht angezeigt, wenn ClickOnce\-Anwendungen nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind.|  
  
 In der folgenden Tabelle wird das Standardverhalten für jede Zone angezeigt.  Die Spalte Anwendungen verweist auf Windows Forms\-Anwendungen, Windows Presentation Foundation\-Anwendungen, WPF\-Browseranwendungen und Konsolenanwendungen.  
  
|Zone|Anwendungen|Office\-Projektmappen|  
|----------|-----------------|---------------------------|  
|`MyComputer`|`Aktiviert`|`Aktiviert`|  
|`LocalIntranet`|`Aktiviert`|`Aktiviert`|  
|`TrustedSites`|`Aktiviert`|`Aktiviert`|  
|`Internet`|`Aktiviert`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Sie können diese Einstellungen überschreiben, indem Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung aktivieren, einschränken oder deaktivieren.  
  
## Aktivieren der vertrauenswürdigen ClickOnce\-Eingabeaufforderung  
 Aktivieren Sie die vertrauenswürdige Eingabeaufforderung für eine Zone, wenn Endbenutzer die Möglichkeit haben sollen, ClickOnce\-Anwendungen aus dieser Zone zu installieren und auszuführen.  
  
#### So aktivieren Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung mit dem Registrierungs\-Editor  
  
1.  Öffnen Sie den Registrierungs\-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie im Feld **Öffnen** den Text `regedit32` ein, und klicken Sie auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3.  Fügen Sie, sofern noch nicht vorhanden, die folgenden Unterschlüssel als **Zeichenfolgenwert** mit den zugeordneten Werten aus folgender Tabelle hinzu.  
  
    |Zeichenfolgenwert\-Unterschlüssel|Wert|  
    |---------------------------------------|----------|  
    |`Internet`|`Aktiviert`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Aktiviert`|  
    |`LocalIntranet`|`Aktiviert`|  
    |`TrustedSites`|`Aktiviert`|  
  
     Standardmäßig besitzt `Internet` bei Office\-Projektmappen den Wert `AuthenticodeRequired`, und `UntrustedSites` besitzt den Wert `Disabled`.  Ansonsten besitzt `Internet` den Standardwert `Enabled`.  
  
#### So aktivieren Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung programmgesteuert  
  
1.  Erstellen Sie in Visual Studio eine Visual Basic\- oder Visual C\#\-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. Program.cs, und fügen Sie den folgenden Code hinzu.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
## Einschränken der vertrauenswürdigen ClickOnce\-Eingabeaufforderung  
 Schränken Sie die vertrauenswürdige Eingabeaufforderung ein, sodass Projektmappen mit Authenticode\-Zertifikaten, deren Identität bekannt ist, signiert sein müssen, bevor Benutzer eine Entscheidung über die Vertrauenswürdigkeit treffen müssen.  
  
#### So schränken Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung mit dem Registrierungs\-Editor ein  
  
1.  Öffnen Sie den Registrierungs\-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie im Feld **Öffnen** den Text `regedit` ein, und klicken Sie auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3.  Fügen Sie, sofern noch nicht vorhanden, die folgenden Unterschlüssel als **Zeichenfolgenwert** mit den zugeordneten Werten aus folgender Tabelle hinzu.  
  
    |Zeichenfolgenwert\-Unterschlüssel|Wert|  
    |---------------------------------------|----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### So schränken Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung programmgesteuert ein  
  
1.  Erstellen Sie in Visual Studio eine Visual Basic\- oder Visual C\#\-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. Program.cs, und fügen Sie den folgenden Code hinzu.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
## Deaktivieren der vertrauenswürdigen ClickOnce\-Eingabeaufforderung  
 Sie können die vertrauenswürdige Eingabeaufforderung deaktivieren, sodass Endbenutzer keine Möglichkeit zum Installieren von Projektmappen haben, die in der Sicherheitsrichtlinie nicht bereits als vertrauenswürdig eingestuft wurden.  
  
#### So deaktivieren Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung mit dem Registrierungs\-Editor  
  
1.  Öffnen Sie den Registrierungs\-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie im Feld **Öffnen** den Text `regedit` ein, und klicken Sie auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3.  Fügen Sie, sofern noch nicht vorhanden, die folgenden Unterschlüssel als **Zeichenfolgenwert** mit den zugeordneten Werten aus folgender Tabelle hinzu.  
  
    |Zeichenfolgenwert\-Unterschlüssel|Wert|  
    |---------------------------------------|----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### So deaktivieren Sie die vertrauenswürdige ClickOnce\-Eingabeaufforderung programmgesteuert  
  
1.  Erstellen Sie in Visual Studio eine Visual Basic\- oder Visual C\#\-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. Program.cs, und fügen Sie den folgenden Code hinzu.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
## Siehe auch  
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce\-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Gewusst wie: Debuggen einer ClickOnce\-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Gewusst wie: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce\-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md)