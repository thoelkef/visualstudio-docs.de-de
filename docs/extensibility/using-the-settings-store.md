---
title: "Verwenden die Einstellungen speichern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Settings-Speicher verwenden"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Verwenden die Einstellungen speichern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es gibt zwei Arten von Einstellungen speichern:  
  
-   Konfigurationseigenschaften, die nur\-Lese Einstellungen für Visual Studio und VSPackages sind. Visual Studio fügt Einstellungen aus allen bekannten PKGDEF\-Dateien in diesem Speicher.  
  
-   Benutzereinstellungen, beschreibbaren Einstellungen wie z. B. diejenigen, die auf Seiten angezeigt werden die **Optionen** im Dialogfeld Eigenschaftenseiten und bestimmte andere Dialogfelder. Visual Studio\-Erweiterungen können diese für die lokale Speicherung von kleinen Datenmengen.  
  
 Diese exemplarische Vorgehensweise veranschaulicht, wie zum Lesen von Daten aus dem Konfigurationsspeicher für die Einstellung. Finden Sie unter [Das Schreiben in die Benutzereinstellungsspeicher](../extensibility/writing-to-the-user-settings-store.md) eine Erläuterung zum Schreiben in den Speicher des Benutzers Einstellungen.  
  
## Erstellen das Beispielprojekt  
 In diesem Abschnitt wird das Erstellen eines einfachen Projekts mit einem Menübefehl zu Demonstrationszwecken veranschaulicht.  
  
1.  Alle Visual Studio\-Erweiterung beginnt mit der ein VSIX\-Bereitstellungsprojekt, das die Ressourcen für die Erweiterung enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX\-Projekt namens `SettingsStoreExtension`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Jetzt fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **SettingsStoreCommand**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Befehl benutzerdefinierte**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **SettingsStoreCommand.cs**. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## Mithilfe der Einstellungen Konfigurationsspeicher  
 Dieser Abschnitt beschreibt das Erkennen und Konfigurationseinstellungen anzeigen.  
  
1.  Fügen Sie in der Datei SettingsStorageCommand.cs die folgende using\-Anweisungen:  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  In `MenuItemCallback`, entfernen Sie den Text der Methode und fügen Sie diese Zeilen erhalten den Einstellungen Konfigurationsspeicher:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     Die <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> ist eine verwaltete Hilfsklasse über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Service.  
  
3.  Jetzt erfahren Sie, ob die Windows Phone\-Tools installiert sind. Der Code sollte wie folgt aussehen:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  Testen Sie den Code. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen SettingsStoreCommand**.  
  
     Daraufhin sollte die Meldung im Feld **Microsoft Windows Phone\-Entwicklertools:**  gefolgt von **True** oder **False**.  
  
 Visual Studio behält die Einstellungen speichern in der Registrierung.  
  
#### Um einen Registrierungs\-Editor verwenden, um Konfigurationen zu überprüfen  
  
1.  Öffnen Sie Regedit.exe.  
  
2.  Navigieren Sie zu HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\.  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass Sie den Schlüssel anzeigen, die \\14.0Exp\_Config\\ und nicht \\14.0\_Config\\ enthält. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, sind Einstellungen in der Registrierungsstruktur "14.0Exp\_Config".  
  
3.  Erweitern Sie den Knoten \\Installed Products\\. Wenn die Nachricht in den vorherigen Schritten **Microsoft Windows Phone Developer Tools installiert: True**, dann \\Installed Products\\ einen Microsoft Windows Phone\-Entwicklertools Knoten enthalten soll. Wenn die Nachricht **Microsoft Windows Phone Developer Tools installiert: False**, und klicken Sie dann \\Installed Products\\ keinen Microsoft Windows Phone\-Entwicklertools Knoten enthalten sein soll.