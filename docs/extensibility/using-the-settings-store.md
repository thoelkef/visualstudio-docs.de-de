---
title: Mit dem Store Einstellungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1d62e3ccc47a2b74629cd1468b023c787a1289e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-settings-store"></a>Mithilfe der Einstellungen für Speicher
Es gibt zwei Arten von Einstellungen speichern:  
  
-   Konfigurationseinstellungen, die nur-Lese Einstellungen für Visual Studio und VSPackage sind. Visual Studio werden die Einstellungen aus allen bekannten PKGDEF-Dateien in diesem Speicher zusammengeführt.  
  
-   Benutzereinstellungen, die beschreibbaren Einstellungen wie z. B. die sind, die auf Seiten angezeigt werden die **Optionen** (Dialogfeld), Eigenschaftenseiten und bestimmte andere Dialogfelder. Visual Studio-Erweiterungen können diese für die lokale Speicherung von kleine Mengen von Daten verwenden.  
  
 In dieser exemplarischen Vorgehensweise wird gezeigt, wie zum Lesen von Daten aus dem Konfigurationsspeicher für die Einstellung. Finden Sie unter [Schreiben in den Speicher des Benutzers Einstellungen](../extensibility/writing-to-the-user-settings-store.md) für eine Erklärung der Vorgehensweise zum Schreiben in den Speicher des Benutzers Einstellungen.  
  
## <a name="creating-the-example-project"></a>Erstellen das Beispielprojekt  
 In diesem Abschnitt wird gezeigt, wie eine Erweiterung für einfachen-Projekt mit einem Menübefehl zu Demonstrationszwecken erstellt.  
  
1.  Alle Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellung-Projekt bzw. die die Erweiterung Ressourcen enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `SettingsStoreExtension`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Fügen Sie jetzt eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **SettingsStoreCommand**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Befehl**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **SettingsStoreCommand.cs**. Weitere Informationen zur Vorgehensweise beim Erstellen eines benutzerdefinierten Befehls finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Mithilfe von Einstellungen für Konfigurationsspeicher  
 In diesem Abschnitt veranschaulicht das Erkennen und Konfigurationseinstellungen anzeigen.  
  
1.  Fügen Sie in der Datei SettingsStorageCommand.cs die folgenden using-Anweisungen:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  In `MenuItemCallback`, entfernen Sie den Text der Methode und fügen Sie diese Zeilen erhalten den Konfigurationsspeicher für die Einstellungen hinzu:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     Die <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> ist eine verwaltete Hilfsklasse über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Dienst.  
  
3.  Nun erfahren Sie, ob die Windows Phone-Tools installiert sind. Der Code sollte wie folgt aussehen:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Testen Sie den Code ein. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  In der experimentellen Instanz auf dem **Tools** Menü klicken Sie auf **aufrufen SettingsStoreCommand**.  
  
     Daraufhin sollte die Meldung Feld **Microsoft Windows Phone-Entwicklertools:** gefolgt von **"true"** oder **"false"**.  
  
 Visual Studio speichert den Store Einstellungen in der systemregistrierung.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Mithilfe ein Registrierungseditors Konfigurationseinstellungen überprüfen  
  
1.  Öffnen Sie Regedit.exe.  
  
2.  Navigieren Sie zu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass Sie den Schlüssel prüfen, die \14.0Exp_Config\ und nicht \14.0_Config enthält\\. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, sind Konfigurationseinstellungen in der Registrierungsstruktur "14.0Exp_Config" ein.  
  
3.  Erweitern Sie den \Installed Products\-Knoten. Wenn die Nachricht in den vorherigen Schritten **Microsoft Windows Phone-Entwickler-Tools installiert: "true"**, dann \Installed Products\ einen Microsoft Windows Phone-Entwicklertools Knoten enthalten soll. Wenn die Nachricht **Microsoft Windows Phone-Entwickler-Tools installiert: "false"**, dann \Installed Products\ einen Microsoft Windows Phone-Entwicklertools-Knoten nicht enthalten soll.