---
title: "Gewusst wie: Konfigurieren der Aufnahmelistensicherheit"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Aufnahmelisten [Office-Entwicklung in Visual Studio]"
  - "Berechtigungen [Office-Entwicklung in Visual Studio]"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Konfigurieren der Aufnahmelistensicherheit
  Mit Administratorrechten können Sie die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung zur Vertrauensstellung konfigurieren, um zu steuern, ob Endbenutzer Office\-Projektmappen installieren dürfen, indem in der Aufnahmeliste eine Entscheidung bezüglich der Vertrauenswürdigkeit gespeichert wird.  Weitere Informationen zu Aufnahmelisten finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Projektmappen in jeder der fünf Zonen können Sie die folgenden Optionen festlegen:  
  
-   Aktivieren Sie den Schlüssel für die vertrauenswürdige [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung und die Aufnahmeliste.  Sie können zulassen, dass Endbenutzer Office\-Projektmappen, die mit einem Zertifikat signiert sind, Vertrauenswürdigkeit gewähren.  
  
-   Schränken Sie den Schlüssel für die vertrauenswürdige [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung und die Aufnahmeliste ein.  Sie können zulassen, dass Endbenutzer Office\-Projektmappen installieren, die mit einem Zertifikat signiert sind, das den Herausgeber identifiziert, aber noch nicht als vertrauenswürdig betrachtet werden.  
  
-   Deaktivieren Sie den Schlüssel für die vertrauenswürdige [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung und die Aufnahmeliste.  Sie können verhindern, dass Endbenutzer Office\-Projektmappen installieren, die nicht mit einem explizit vertrauenswürdigen Zertifikat signiert sind.  
  
## Aktivieren der Aufnahmeliste  
 Aktivieren Sie die Aufnahmeliste für eine Zone, wenn Endbenutzer die Möglichkeit haben sollen, Office\-Projektmappen aus dieser Zone zu installieren und auszuführen.  
  
#### So aktivieren Sie die Aufnahmeliste mithilfe des Registrierungs\-Editors  
  
1.  Öffnen Sie den Registrierungs\-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie **regedt32.exe** im Feld **Öffnen** ein, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert** mit den zugeordneten Werten hinzu, wenn sie nicht bereits vorhanden sind.  
  
    |Zeichenfolgenwert\-Unterschlüssel|Wert|  
    |---------------------------------------|----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Aktiviert**|  
    |**LocalIntranet**|**Aktiviert**|  
    |**TrustedSites**|**Aktiviert**|  
  
     Standardmäßig besitzt **Internet** den Wert **AuthenticodeRequired**, und **UntrustedSites** besitzt den Wert **Disabled**.  
  
#### So aktivieren Sie die Aufnahmeliste programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic\- oder Visual C\#\-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. Program.cs, und fügen Sie den folgenden Code hinzu.  
  
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
  
## Einschränken der Aufnahmeliste  
 Schränken Sie die Aufnahmeliste ein, sodass Projektmappen mit Authenticode\-Zertifikaten, deren Identität bekannt ist, signiert sein müssen, bevor Benutzer Entscheidung über die Vertrauenswürdigkeit treffen müssen.  
  
#### So schränken Sie die Aufnahmeliste ein  
  
1.  Öffnen Sie den Registrierungs\-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie **regedt32.exe** im Feld **Öffnen** ein, und klicken Sie dann auf **OK**.  
  
2.  Suchen Sie den folgenden Registrierungsschlüssel:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Wenn der Schlüssel nicht vorhanden ist, erstellen Sie ihn.  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert** mit den zugeordneten Werten hinzu, wenn sie nicht bereits vorhanden sind.  
  
    |Zeichenfolgenwert\-Unterschlüssel|Wert|  
    |---------------------------------------|----------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Standardmäßig besitzt **Internet** den Wert **AuthenticodeRequired**, und **UntrustedSites** besitzt den Wert **Disabled**.  
  
#### So schränken Sie die Aufnahmeliste programmgesteuert ein  
  
1.  Erstellen Sie eine Visual Basic\- oder Visual C\#\-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. Program.cs, und fügen Sie den folgenden Code hinzu.  
  
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
  
## Deaktivieren der Aufnahmeliste  
 Sie können die Aufnahmeliste deaktivieren, sodass Endbenutzer nur Projektmappen installieren können, die mit einem vertrauenswürdigen und bekannten Zertifikat signiert sind.  
  
#### So deaktivieren Sie die Aufnahmeliste  
  
1.  Öffnen Sie den Registrierungs\-Editor:  
  
    1.  Klicken Sie auf **Start** und dann auf **Ausführen**.  
  
    2.  Geben Sie **regedt32.exe** im Feld **Öffnen** ein, und klicken Sie dann auf **OK**.  
  
2.  Erstellen Sie den folgenden Registrierungsschlüssel, wenn dieser nicht bereits vorhanden ist:  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  Fügen Sie die folgenden Unterschlüssel als **Zeichenfolgenwert** mit den zugeordneten Werten hinzu, wenn sie nicht bereits vorhanden sind.  
  
    |Zeichenfolgenwert\-Unterschlüssel|Wert|  
    |---------------------------------------|----------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**LocalIntranet**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### So deaktivieren Sie die Aufnahmeliste programmgesteuert  
  
1.  Erstellen Sie eine Visual Basic\- oder Visual C\#\-Konsolenanwendung.  
  
2.  Öffnen Sie die Datei Program.vb bzw. Program.cs, und fügen Sie den folgenden Code hinzu.  
  
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
  
## Siehe auch  
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen mithilfe von Aufnahmelisten](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  