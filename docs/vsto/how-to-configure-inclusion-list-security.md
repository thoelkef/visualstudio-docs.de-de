---
title: 'Gewusst wie: Konfigurieren der aufnahmelistensicherheit'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e5bd1794b76485d60588b94d3ca139a314f9723
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255836"
---
# <a name="how-to-configure-inclusion-list-security"></a>Gewusst wie: Konfigurieren der aufnahmelistensicherheit
  Wenn Sie über Administratorberechtigungen verfügen, können Sie konfigurieren die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdige Eingabeaufforderung um zu steuern, ob der Endbenutzer die Möglichkeit, Office-Projektmappen installieren, indem Sie eine Entscheidung über die Vertrauenswürdigkeit in der Aufnahmeliste speichern angegeben werden. Weitere Informationen zu Aufnahmelisten, finden Sie unter [vertrauen Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Lösungen, die in jeder der fünf Zonen sind, können Sie die folgenden Optionen festlegen:  
  
-   Aktivieren der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Eingabeaufforderung Schlüssel vertrauen und die Aufnahmeliste. Sie können die Benutzer zum Gewähren von Vertrauenswürdigkeit für Office-Projektmappen, die mit einem Zertifikat signiert sind.  
  
-   Einschränken der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Eingabeaufforderung Schlüssel vertrauen und die Aufnahmeliste. Sie können Endbenutzern gestatten, die Office-Projektmappen, die signiert sind, die den Verleger identifiziert, aber das ist nicht bereits vertrauenswürdig, mit einem Zertifikat zu installieren.  
  
-   Deaktivieren Sie die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Eingabeaufforderung Schlüssel vertrauen und die Aufnahmeliste. Sie können verhindern, dass Benutzer Office-Projektmappen, die nicht signiert ist mit einem explizit vertrauenswürdigen Zertifikat installieren.  
  
## <a name="enable-the-inclusion-list"></a>Ermöglichen der Aufnahmeliste  
 Aktivieren Sie die Aufnahmeliste für eine Zone aus, wenn der Endbenutzer angezeigt werden, mit der Option installieren und Ausführen von Office-Projektmappen, die von dieser Zone stammen sollen.  
  
### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>So aktivieren Sie die Aufnahmeliste mit dem Registrierungs-editor  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben **regedt32.exe**, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugehörigen Werten vorhanden sind.  
  
    |Unterschlüssel für Zeichenfolge-Wert|Wert|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled** (deaktiviert)|  
    |**Arbeitsplatz**|**Aktiviert**|  
    |**LocalIntranet**|**Aktiviert**|  
    |**TrustedSites**|**Aktiviert**|  
  
     In der Standardeinstellung **Internet** hat den Wert **AuthenticodeRequired** und **UntrustedSites** hat den Wert **deaktiviert**.  
  
### <a name="to-enable-the-inclusion-list-programmatically"></a>Um die Aufnahmeliste programmgesteuert zu aktivieren.  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung.  
  
2.  Öffnen der *Program.vb* oder *"Program.cs"* -Datei zur Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
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
  
## <a name="restrict-the-inclusion-list"></a>Einschränken der Aufnahmeliste  
 Schränken Sie die Aufnahmeliste, sodass Lösungen mit Authenticode-Zertifikaten signiert werden müssen, die Identität bekannt waren, bevor eine Entscheidung über die Vertrauenswürdigkeit abgefragt werden.  
  
### <a name="to-restrict-the-inclusion-list"></a>Zum Einschränken der Aufnahmeliste  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben **regedt32.exe**, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn aus.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugehörigen Werten vorhanden sind.  
  
    |Unterschlüssel für Zeichenfolge-Wert|Wert|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Disabled** (deaktiviert)|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Arbeitsplatz**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     In der Standardeinstellung **Internet** hat den Wert **AuthenticodeRequired** und **UntrustedSites** hat den Wert **deaktiviert**.  
  
### <a name="to-restrict-the-inclusion-list-programmatically"></a>Um die Aufnahmeliste programmgesteuert zu beschränken.  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung.  
  
2.  Öffnen der *Program.vb* oder *"Program.cs"* -Datei zur Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
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
  
## <a name="disable-the-inclusion-list"></a>Deaktivieren der Aufnahmeliste  
 Sie können die Aufnahmeliste deaktivieren, damit Endbenutzer nur installieren können Lösungen, die signiert sind mit einem vertrauenswürdigen und bekannten Zertifikat.  
  
### <a name="to-disable-the-inclusion-list"></a>So deaktivieren Sie die Aufnahmeliste  
  
1.  Öffnen Sie den Registrierungs-Editor ein:  
  
    1.  Klicken Sie auf **starten**, und klicken Sie dann auf **ausführen**.  
  
    2.  In der **öffnen** geben **regedt32.exe**, und klicken Sie dann auf **OK**.  
  
2.  Erstellen Sie den folgenden Registrierungsschlüssel aus, wenn dies nicht bereits vorhanden ist:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert**, wenn sie nicht bereits mit den zugehörigen Werten vorhanden sind.  
  
    |Unterschlüssel für Zeichenfolge-Wert|Wert|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Disabled** (deaktiviert)|  
    |**Internet**|**Disabled** (deaktiviert)|  
    |**Arbeitsplatz**|**Disabled** (deaktiviert)|  
    |**LocalIntranet**|**Disabled** (deaktiviert)|  
    |**TrustedSites**|**Disabled** (deaktiviert)|  
  
### <a name="to-disable-the-inclusion-list-programmatically"></a>So deaktivieren Sie die Aufnahmeliste programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic oder Visual C#-Konsolenanwendung.  
  
2.  Öffnen der *Program.vb* oder *"Program.cs"* -Datei zur Bearbeitung, und fügen Sie den folgenden Code hinzu.  
  
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
 [Vertrauen Sie Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  