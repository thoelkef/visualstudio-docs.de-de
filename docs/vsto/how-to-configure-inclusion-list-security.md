---
title: 'Vorgehensweise: Konfigurieren der Aufnahmelistensicherheit | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0b95b85f028ac003cedb05248b6884c24ca32008
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-configure-inclusion-list-security"></a>Gewusst wie: Konfigurieren der Aufnahmelistensicherheit
  Wenn Sie über Administratorberechtigungen verfügen, können Sie konfigurieren die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdige Eingabeaufforderung steuern, ob Endbenutzer die Möglichkeit, installieren Office-Projektmappen durch das Speichern einer Entscheidung über die Vertrauenswürdigkeit der Aufnahmeliste angegeben werden. Informationen zu Aufnahmelisten finden Sie unter [vertrauen Office-Projektmappen mithilfe von Benutzeraufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Lösungen, die in jeder der fünf Zonen sind, können Sie die folgenden Optionen festlegen:  
  
-   Aktivieren der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Prompt Schlüssel vertrauen und die Aufnahmeliste. Sie können die Endbenutzer zum Gewähren von Vertrauenswürdigkeit für Office-Projektmappen, die mit einem Zertifikat signiert sind.  
  
-   Einschränken der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Prompt Schlüssel vertrauen und die Aufnahmeliste. Sie können die Endbenutzer zum Installieren von Office-Projektmappen, die signiert sind mit einem Zertifikat, den Herausgeber identifiziert, aber das ist nicht bereits vertrauenswürdigen, erlauben.  
  
-   Deaktivieren der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Prompt Schlüssel vertrauen und die Aufnahmeliste. Sie können verhindern, dass Endbenutzer keine Office-Projektmappen, die nicht signiert ist mit einem explizit vertrauenswürdigen Zertifikat installieren.  
  
## <a name="enabling-the-inclusion-list"></a>Aktivieren der Aufnahmeliste  
 Aktivieren Sie die Aufnahmeliste für eine Zone aus, wenn der Endbenutzer dargestellt werden, mit der Option für die Installation und Ausführung von Office-Projektmappen, die von dieser Zone stammen sollen.  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>So aktivieren Sie die Aufnahmeliste mit dem Registrierungs-editor  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben **regedt32.exe**, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, sofern sie nicht bereits, mit den zugehörigen Werten vorhanden sind.  
  
    |String-Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled** (deaktiviert)|  
    |**MyComputer**|**Aktiviert**|  
    |**LocalIntranet**|**Aktiviert**|  
    |**TrustedSites**|**Aktiviert**|  
  
     Standardmäßig **Internet** hat den Wert **AuthenticodeRequired** und **UntrustedSites** hat den Wert **deaktiviert**.  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>So aktivieren Sie die Aufnahmeliste programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. "Program.cs" für die Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
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
  
## <a name="restricting-the-inclusion-list"></a>Einschränken der Aufnahmeliste  
 Schränken Sie die Aufnahmeliste, sodass Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die Identität bekannt sind, bevor eine Entscheidung über die Vertrauenswürdigkeit abgefragt werden.  
  
#### <a name="to-restrict-the-inclusion-list"></a>Zum Einschränken der Aufnahmeliste  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben **regedt32.exe**, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, sofern sie nicht bereits, mit den zugehörigen Werten vorhanden sind.  
  
    |String-Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Disabled** (deaktiviert)|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Standardmäßig **Internet** hat den Wert **AuthenticodeRequired** und **UntrustedSites** hat den Wert **deaktiviert**.  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>So schränken Sie die Aufnahmeliste programmgesteuert ein  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung.  
  
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
  
## <a name="disabling-the-inclusion-list"></a>Deaktivieren der Aufnahmeliste  
 Sie können die Aufnahmeliste deaktivieren, sodass Endbenutzer nur Projektmappen installieren können, die signiert sind mit einem Zertifikat eines vertrauenswürdigen und bekannten.  
  
#### <a name="to-disable-the-inclusion-list"></a>So deaktivieren Sie die Aufnahmeliste  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben **regedt32.exe**, und klicken Sie dann auf **OK**.  
  
2.  Erstellen Sie den folgenden Registrierungsschlüssel aus, wenn dies nicht bereits vorhanden ist:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, sofern sie nicht bereits, mit den zugehörigen Werten vorhanden sind.  
  
    |String-Wert-Unterschlüssel|Wert|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Disabled** (deaktiviert)|  
    |**Internet**|**Disabled** (deaktiviert)|  
    |**MyComputer**|**Disabled** (deaktiviert)|  
    |**LocalIntranet**|**Disabled** (deaktiviert)|  
    |**TrustedSites**|**Disabled** (deaktiviert)|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>So deaktivieren Sie die Aufnahmeliste programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung.  
  
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
 [Gewähren von Vertrauenswürdigkeit Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  