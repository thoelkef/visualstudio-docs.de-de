---
title: 'Vorgehensweise: Konfigurieren Sie das Verhalten der Authentifizierungeingabeaufforderung ClickOnce Vertrauensstellung | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 8822d0aa9947dccbdfabc43d7090b52eba7d0844
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Gewusst wie: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit
Sie können die ClickOnce-vertrauensaufforderung Steuerelement konfigurieren Sie, ob Endbenutzer die Möglichkeit, installieren die ClickOnce-Anwendungen, z. B. Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen, WPF-Browser angegeben werden Anwendungen und Office-Projektmappen. Konfigurieren Sie die vertrauenswürdige Eingabeaufforderung durch Festlegen von Registrierungsschlüsseln auf jedes Endbenutzers Computer.  
  
 Die folgende Tabelle zeigt die Konfigurationsoptionen, die auf jede der fünf Zonen (Internet, UntrustedSites, MyComputer, LocalIntranet und TrustedSites) angewendet werden können.  
  
|Option|Registrierungswert "Einstellung"|Beschreibung|  
|------------|----------------------------|-----------------|  
|Aktivieren Sie die vertrauenswürdige Eingabeaufforderung.|`Enabled`|ClickOnce-vertrauensaufforderung ist angezeigt, sodass Endbenutzer Vertrauenswürdigkeit ClickOnce-Anwendung gewähren können.|  
|Schränken Sie die vertrauenswürdige Eingabeaufforderung.|`AuthenticodeRequired`|ClickOnce-vertrauensaufforderung wird nur angezeigt, wenn die ClickOnce-Anwendungen mit einem Zertifikat signiert sind, die den Herausgeber identifiziert.|  
|Deaktivieren Sie die vertrauenswürdige Eingabeaufforderung.|`Disabled`|ClickOnce-vertrauensaufforderung wird nicht für eine ClickOnce-Anwendungen angezeigt, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind.|  
  
 Die folgende Tabelle zeigt das Standardverhalten für jede Zone. Die Anwendungen Spalte bezieht sich auf Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, WPF-Webbrowseranwendungen und konsolenanwendungen.  
  
|Zone|Anwendungen|Office-Projektmappen|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Sie können diese Einstellungen überschreiben, indem aktivieren, beschränken oder deaktivieren die ClickOnce-vertrauensaufforderung.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Aktivieren die ClickOnce-Vertrauensaufforderung  
 Aktivieren Sie die vertrauenswürdige Eingabeaufforderung für eine Zone aus, wenn Endbenutzer die Möglichkeit, installieren und Ausführen einer beliebigen ClickOnce-Anwendung, die von dieser Zone stammen angezeigt werden sollen.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So aktivieren Sie die ClickOnce-vertrauensaufforderung mithilfe des Registrierungs-Editors  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben `regedit32`, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, sofern sie nicht bereits, mit den zugehörigen Werten in der folgenden Tabelle aufgeführten vorhanden sind.  
  
    |String-Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Für Office-Projektmappen `Internet` hat den Standardwert `AuthenticodeRequired` und `UntrustedSites` hat den Wert `Disabled`. Für alle anderen `Internet` hat den Standardwert `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>So aktivieren Sie die ClickOnce-vertrauensaufforderung programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung in Visual Studio.  
  
2.  Öffnen Sie die Datei Program.vb bzw. "Program.cs" für die Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Beschränken die ClickOnce-Vertrauensaufforderung  
 Schränken Sie die vertrauenswürdige Eingabeaufforderung aus, sodass Sie Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die Identität bekannt sind, bevor eine Entscheidung über die Vertrauenswürdigkeit abgefragt werden.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Um die ClickOnce-vertrauensaufforderung einschränken, indem Sie mithilfe des Registrierungs-Editors  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben `regedit`, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, sofern sie nicht bereits, mit den zugehörigen Werten in der folgenden Tabelle aufgeführten vorhanden sind.  
  
    |String-Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Um die ClickOnce-vertrauensaufforderung programmgesteuert zu beschränken.  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung in Visual Studio.  
  
2.  Öffnen Sie die Datei Program.vb bzw. "Program.cs" für die Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Deaktivieren die ClickOnce-Vertrauensaufforderung  
 Sie können die vertrauenswürdige Eingabeaufforderung deaktivieren, sodass Endbenutzer nicht angegeben, werden die Option zum Installieren von Lösungen, die bereits in ihrer Sicherheitsrichtlinie nicht vertrauenswürdig sind.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So deaktivieren Sie die ClickOnce-vertrauensaufforderung mithilfe des Registrierungs-Editors  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben `regedit`, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, sofern sie nicht bereits, mit den zugehörigen Werten in der folgenden Tabelle aufgeführten vorhanden sind.  
  
    |String-Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>So deaktivieren Sie die ClickOnce-vertrauensaufforderung programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung in Visual Studio.  
  
2.  Öffnen Sie die Datei Program.vb bzw. "Program.cs" für die Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings (Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen)](../deployment/how-to-enable-clickonce-security-settings.md)   
 [How to: Set a Security Zone for a ClickOnce Application (Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung)](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application (Vorgehensweise: Festlegen von benutzerdefinierten Berechtigungen für eine ClickOnce-Anwendung)](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [How to: Debug a ClickOnce Application with Restricted Permissions (Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen)](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Gewusst wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)