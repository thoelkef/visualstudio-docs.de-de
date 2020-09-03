---
title: 'Gewusst wie: Konfigurieren des Verhaltens der ClickOnce-Vertrauens Aufforderung | Microsoft-Dokumentation'
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
ms.openlocfilehash: 58e5f0e9154137097a94637799966ee94818fca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150828"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Gewusst wie: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die ClickOnce-Vertrauensstellungs Aufforderung konfigurieren, um zu steuern, ob Endbenutzer die Möglichkeit haben, ClickOnce-Anwendungen zu installieren, z. b. Windows Forms Anwendungen, Windows Presentation Foundation Anwendungen, Konsolen Anwendungen, WPF-Browser Anwendungen und Office-Projektmappen. Sie konfigurieren die Vertrauensstellungs-Eingabeaufforderung, indem Sie auf jedem Computer des Endbenutzers Registrierungsschlüssel festlegen.  
  
 In der folgenden Tabelle sind die Konfigurationsoptionen aufgeführt, die auf jede der fünf Zonen (Internet, untreuhänder, MyComputer, LocalIntranet und Treuhänder) angewendet werden können.  
  
|Option|Registrierungs Einstellungs Wert|Beschreibung|  
|------------|----------------------------|-----------------|  
|Aktivieren Sie die Vertrauensstellungs Aufforderung.|`Enabled`|Die Eingabeaufforderung für die ClickOnce-Vertrauensstellung wird angezeigt, sodass Endbenutzer den ClickOnce-Anwendungen Vertrauen gewähren können.|  
|Beschränken Sie die Vertrauensstellungs Aufforderung.|`AuthenticodeRequired`|Die ClickOnce-Vertrauensstellungs Aufforderung wird nur angezeigt, wenn ClickOnce-Anwendungen mit einem Zertifikat signiert sind, das den Verleger identifiziert.|  
|Deaktivieren Sie die Vertrauensstellungs Aufforderung.|`Disabled`|Die ClickOnce-Vertrauensstellungs Aufforderung wird für keine ClickOnce-Anwendungen angezeigt, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind.|  
  
 In der folgenden Tabelle wird das Standardverhalten für jede Zone angezeigt. Die Spalte Anwendungen bezieht sich auf Windows Forms Anwendungen, Windows Presentation Foundation Anwendungen, WPF-Browser Anwendungen und Konsolen Anwendungen.  
  
|Zone|Applications|Office-Projektmappen|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Sie können diese Einstellungen überschreiben, indem Sie die ClickOnce-Vertrauensstellungs Aufforderung aktivieren, einschränken oder deaktivieren.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Aktivieren der ClickOnce-Vertrauensstellungs Aufforderung  
 Aktivieren Sie die Vertrauensstellungs Aufforderung für eine Zone, wenn Sie möchten, dass Endbenutzer eine beliebige ClickOnce-Anwendung installieren und ausführen, die aus dieser Zone stammt.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So aktivieren Sie die ClickOnce-Vertrauensstellungs Aufforderung mithilfe des Registrierungs-Editors  
  
1. Öffnen Sie den Registrierungs-Editor:  
  
    1. Klicken Sie im **Startmenü**auf **Ausführen**.  
  
    2. Geben Sie im Feld **Öffnen** `regedit` (oder `regedit32` 32-Bit-Windows) ein, und klicken Sie dann auf **OK**.  
  
2. Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3. Fügen Sie die folgenden Unterschlüssel als **Zeichen folgen Wert**hinzu, wenn Sie nicht bereits vorhanden sind, und geben Sie die zugehörigen Werte in der folgenden Tabelle ein.  
  
    |Zeichen folgen Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Für Office-Projektmappen `Internet` hat den Standardwert `AuthenticodeRequired` und `UntrustedSites` hat den Wert `Disabled` . Für alle anderen `Internet` verfügt über den Standardwert `Enabled` .  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>So aktivieren Sie die ClickOnce-Vertrauensstellungs Aufforderung Programm gesteuert  
  
1. Erstellen Sie eine Visual Basic-oder Visual c#-Konsolenanwendung in Visual Studio.  
  
2. Öffnen Sie die Datei "Program. vb" oder "Program.cs" zum Bearbeiten, und fügen Sie folgenden Code hinzu.  
  
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
  
3. Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Einschränken der ClickOnce-Vertrauensstellungs Aufforderung  
 Schränken Sie die Vertrauensstellungs Aufforderung ein, damit Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die über eine bekannte Identität verfügen, bevor Benutzer zur Eingabe einer Vertrauens Entscheidung aufgefordert werden  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So schränken Sie die ClickOnce-Vertrauensstellungs Aufforderung mithilfe des Registrierungs-Editors ein  
  
1. Öffnen Sie den Registrierungs-Editor:  
  
    1. Klicken Sie im **Startmenü**auf **Ausführen**.  
  
    2. Geben Sie im Feld **Öffnen** `regedit` (oder `regedit32` 32-Bit-Windows) ein, und klicken Sie dann auf **OK**.  
  
2. Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3. Fügen Sie die folgenden Unterschlüssel als **Zeichen folgen Wert**hinzu, wenn Sie nicht bereits vorhanden sind, und geben Sie die zugehörigen Werte in der folgenden Tabelle ein.  
  
    |Zeichen folgen Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>So schränken Sie die ClickOnce-Vertrauensstellungs Aufforderung Programm gesteuert ein  
  
1. Erstellen Sie eine Visual Basic-oder Visual c#-Konsolenanwendung in Visual Studio.  
  
2. Öffnen Sie die Datei "Program. vb" oder "Program.cs" zum Bearbeiten, und fügen Sie folgenden Code hinzu.  
  
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
  
3. Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Deaktivieren der ClickOnce-Vertrauensstellungs Aufforderung  
 Sie können die Vertrauensstellungs Aufforderung deaktivieren, damit Endbenutzern nicht die Option erteilt wird, Lösungen zu installieren, die in Ihrer Sicherheitsrichtlinie nicht bereits vertraut sind.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So deaktivieren Sie die ClickOnce-Vertrauensstellungs Aufforderung mithilfe des Registrierungs-Editors  
  
1. Öffnen Sie den Registrierungs-Editor:  
  
    1. Klicken Sie im **Startmenü**auf **Ausführen**.  
  
    2. Geben Sie im Feld **Öffnen** `regedit` (oder `regedit32` 32-Bit-Windows) ein, und klicken Sie dann auf **OK**.  
  
2. Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3. Fügen Sie die folgenden Unterschlüssel als **Zeichen folgen Wert**hinzu, wenn Sie nicht bereits vorhanden sind, und geben Sie die zugehörigen Werte in der folgenden Tabelle ein.  
  
    |Zeichen folgen Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>So deaktivieren Sie die ClickOnce-Vertrauensstellungs Aufforderung Programm gesteuert  
  
1. Erstellen Sie eine Visual Basic-oder Visual c#-Konsolenanwendung in Visual Studio.  
  
2. Öffnen Sie die Datei "Program. vb" oder "Program.cs" zum Bearbeiten, und fügen Sie folgenden Code hinzu.  
  
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
  
3. Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Zugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Übersicht über bereit Stellungen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Vorgehensweise: Festlegen einer Sicherheits Zone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Client Computer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Vorgehensweise: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
