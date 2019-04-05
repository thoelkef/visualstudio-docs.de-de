---
title: 'Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce-Vertrauensstellung Prompt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5a1174f96e34773aac524562d6f62514e92ba5e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "59001167"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die ClickOnce-vertrauensaufforderung, um zu steuern konfigurieren, ob Benutzer die Option zum Installieren der ClickOnce-Anwendungen, z. B. Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen, WPF-Browser angegeben werden Anwendungen und Office-Projektmappen. Sie konfigurieren die vertrauenswürdige Eingabeaufforderung durch Festlegen von Registrierungsschlüsseln für jeden Computer des Benutzers.  
  
 Die folgende Tabelle zeigt die Konfigurationsoptionen, die auf jede der fünf Zonen (Internet, UntrustedSites, Arbeitsplatz, LocalIntranet und TrustedSites) angewendet werden können.  
  
|Option|Festlegen des Registrierungswerts|Beschreibung|  
|------------|----------------------------|-----------------|  
|Ermöglichen Sie die vertrauenswürdige Eingabeaufforderung.|`Enabled`|Der ClickOnce-vertrauensaufforderung ist angezeigt, sodass Endbenutzer Vertrauensstellung für ClickOnce-Anwendungen erteilen können.|  
|Beschränken Sie die vertrauenswürdige Eingabeaufforderung.|`AuthenticodeRequired`|Der ClickOnce-vertrauensaufforderung wird nur angezeigt, wenn die ClickOnce-Anwendungen mit einem Zertifikat signiert sind, die den Herausgeber identifiziert.|  
|Deaktivieren Sie die vertrauenswürdige Eingabeaufforderung.|`Disabled`|Der ClickOnce-vertrauensaufforderung wird nicht für jede ClickOnce-Anwendungen angezeigt, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind.|  
  
 Die folgende Tabelle zeigt das Standardverhalten für jede Zone. Die Spalte Anwendungen bezieht sich auf Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen und WPF-Webbrowseranwendungen.  
  
|Zone|Anwendungen|Office-Projektmappen|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Sie können diese Einstellungen überschreiben, indem aktivieren, beschränken oder der ClickOnce-vertrauensaufforderung deaktivieren.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Aktivieren der ClickOnce-Vertrauensaufforderung  
 Aktivieren Sie die vertrauenswürdige Eingabeaufforderung für eine Zone aus, wenn der Endbenutzer mit der Option installieren und Ausführen einer beliebigen ClickOnce-Anwendung, die von dieser Zone ist angezeigt werden sollen.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Um die ClickOnce-vertrauensaufforderung zu aktivieren, indem Sie den Registrierungs-editor  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  In der **öffnen** geben `regedit` (oder `regedit32` auf 32-Bit-Windows), und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugeordneten, in der folgenden Tabelle angezeigten Werten vorhanden sind.  
  
    |Unterschlüssel für Zeichenfolge-Wert|Wert|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Bei Office-Projektmappen `Internet` hat den Standardwert `AuthenticodeRequired` und `UntrustedSites` hat den Wert `Disabled`. Für alle anderen `Internet` hat den Standardwert `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Um die ClickOnce-vertrauensaufforderung programmgesteuert zu aktivieren.  
  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Einschränken der ClickOnce-Vertrauensaufforderung  
 Schränken Sie die vertrauenswürdige Eingabeaufforderung aus, sodass Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die Identität bekannt waren, bevor eine Entscheidung über die Vertrauenswürdigkeit abgefragt werden.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Um die ClickOnce-vertrauensaufforderung zu beschränken, indem Sie den Registrierungs-editor  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  In der **öffnen** geben `regedit` (oder `regedit32` auf 32-Bit-Windows), und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugeordneten, in der folgenden Tabelle angezeigten Werten vorhanden sind.  
  
    |Unterschlüssel für Zeichenfolge-Wert|Wert|  
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
 Sie können die vertrauenswürdige Eingabeaufforderung deaktivieren, damit Endbenutzer nicht erhalten, dass die Option zum Installieren von Lösungen, die bereits in ihrer Sicherheitsrichtlinie nicht vertraut wird.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So deaktivieren Sie die ClickOnce-vertrauensaufforderung mithilfe des Registrierungs-Editors  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  In der **öffnen** geben `regedit` (oder `regedit32` auf 32-Bit-Windows), und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugeordneten, in der folgenden Tabelle angezeigten Werten vorhanden sind.  
  
    |Unterschlüssel für Zeichenfolge-Wert|Wert|  
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
 [Vorgehensweise: ClickOnce-Sicherheitseinstellungen aktivieren](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Vorgehensweise: Festlegen Sie benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
