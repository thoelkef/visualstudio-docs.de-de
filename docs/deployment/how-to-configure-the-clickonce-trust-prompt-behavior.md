---
title: 'Gewusst wie: Konfigurieren des ClickOnce-Vertrauensaufforderungsverhaltens | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649159"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit
Sie können die ClickOnce-Vertrauensaufforderung konfigurieren, um zu steuern, ob Endbenutzer die Möglichkeit erhalten, ClickOnce-Anwendungen wie Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, Konsolenanwendungen, WPF-Browseranwendungen und Office-Lösungen zu installieren. Sie konfigurieren die Vertrauensaufforderung, indem Sie Registrierungsschlüssel auf dem Computer jedes Endbenutzers festlegen.

 Die folgende Tabelle zeigt die Konfigurationsoptionen, die auf jede der fünf Zonen angewendet werden können (Internet, Nicht vertrauenswürdige Sites, MyComputer, LocalIntranet und TrustedSites).

|Option|Registrierungseinstellungswert|BESCHREIBUNG|
|------------|----------------------------|-----------------|
|Aktivieren Sie die Vertrauensaufforderung.|`Enabled`|Die ClickOnce-Vertrauensaufforderung wird angezeigt, damit Endbenutzer ClickOnce-Anwendungen Vertrauen gewähren können.|
|Beschränken Sie die Vertrauensaufforderung.|`AuthenticodeRequired`|Die ClickOnce-Vertrauensaufforderung wird nur angezeigt, wenn ClickOnce-Anwendungen mit einem Zertifikat signiert sind, das den Herausgeber identifiziert.|
|Deaktivieren Sie die Vertrauensaufforderung.|`Disabled`|Die ClickOnce-Vertrauensaufforderung wird für ClickOnce-Anwendungen, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind, nicht angezeigt.|

 Die folgende Tabelle zeigt das Standardverhalten für jede Zone. Die Spalte Anwendungen bezieht sich auf Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, WPF-Browseranwendungen und Konsolenanwendungen.

|Zone|Anwendungen|Office-Projektmappen|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Sie können diese Einstellungen überschreiben, indem Sie die ClickOnce-Vertrauensaufforderung aktivieren, einschränken oder deaktivieren.

## <a name="enable-the-clickonce-trust-prompt"></a>Aktivieren der ClickOnce-Vertrauensaufforderung
 Aktivieren Sie die Vertrauensaufforderung für eine Zone, wenn Endbenutzern die Option zum Installieren und Ausführen einer ClickOnce-Anwendung angezeigt werden soll, die aus dieser Zone stammt.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So aktivieren Sie die ClickOnce-Vertrauensaufforderung mithilfe des Registrierungs-Editors

1. Öffnen Sie den Registrierungseditor:

    1. Klicken Sie auf **Start** und dann auf **Ausführen**.

    2. Geben **Open** Sie `regedit`im Feld Öffnen ein, und klicken Sie dann auf **OK**.

2. Finden Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert hinzu,** falls sie noch nicht vorhanden sind, mit den in der folgenden Tabelle angezeigten zugehörigen Werten.

    |Unterschlüssel String-Wert|Wert|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Für `Internet` Office-Lösungen, hat `AuthenticodeRequired` `UntrustedSites` den Standardwert und hat den Wert `Disabled`. Für alle `Internet` anderen, hat `Enabled`den Standardwert .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>So aktivieren Sie die ClickOnce-Vertrauensaufforderung programmgesteuert

1. Erstellen Sie in Visual Studio eine Visual Basic- oder Visual C-Konsolenanwendung.

2. Öffnen Sie die *Datei Program.vb* oder *Program.cs* sie bearbeiten, und fügen Sie den folgenden Code hinzu.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Beschränken der ClickOnce-Vertrauensaufforderung
 Beschränken Sie die Vertrauensaufforderung, sodass Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die eine bekannte Identität haben, bevor Benutzer zur Eingabe einer Vertrauensentscheidung aufgefordert werden.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So beschränken Sie die ClickOnce-Vertrauensaufforderung mithilfe des Registrierungs-Editors

1. Öffnen Sie den Registrierungseditor:

    1. Klicken Sie auf **Start** und dann auf **Ausführen**.

    2. Geben **Open** Sie `regedit`im Feld Öffnen ein, und klicken Sie dann auf **OK**.

2. Finden Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert hinzu,** falls sie noch nicht vorhanden sind, mit den in der folgenden Tabelle angezeigten zugehörigen Werten.

    |Unterschlüssel String-Wert|Wert|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>So beschränken Sie die ClickOnce-Vertrauensaufforderung programmgesteuert

1. Erstellen Sie in Visual Studio eine Visual Basic- oder Visual C-Konsolenanwendung.

2. Öffnen Sie die *Datei Program.vb* oder *Program.cs* sie bearbeiten, und fügen Sie den folgenden Code hinzu.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Deaktivieren der ClickOnce-Vertrauensaufforderung
 Sie können die Vertrauensaufforderung deaktivieren, damit Endbenutzer nicht die Möglichkeit erhalten, Lösungen zu installieren, die in ihrer Sicherheitsrichtlinie noch nicht vertrauenswürdig sind.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>So deaktivieren Sie die ClickOnce-Vertrauensaufforderung mithilfe des Registrierungs-Editors

1. Öffnen Sie den Registrierungseditor:

    1. Klicken Sie auf **Start** und dann auf **Ausführen**.

    2. Geben **Open** Sie `regedit`im Feld Öffnen ein, und klicken Sie dann auf **OK**.

2. Finden Sie den folgenden Registrierungsschlüssel:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.

3. Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert hinzu,** falls sie noch nicht vorhanden sind, mit den in der folgenden Tabelle angezeigten zugehörigen Werten.

    |Unterschlüssel String-Wert|Wert|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>So deaktivieren Sie die ClickOnce-Vertrauensaufforderung programmgesteuert

1. Erstellen Sie in Visual Studio eine Visual Basic- oder Visual C-Konsolenanwendung.

2. Öffnen Sie die *Datei Program.vb* oder *Program.cs* sie bearbeiten, und fügen Sie den folgenden Code hinzu.

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

## <a name="see-also"></a>Siehe auch
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)
- [Übersicht über das Bereitstellen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)
- [Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen](../deployment/how-to-enable-clickonce-security-settings.md)
- [Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Vorgehensweise: Festlegen von benutzerdefinierten Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](securing-clickonce-applications.md)
- [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
