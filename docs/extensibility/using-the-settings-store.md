---
title: Verwenden die Store-Einstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72bfc23f585506d86a485d325611c9281f49a51d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949213"
---
# <a name="using-the-settings-store"></a>Verwenden des Einstellungsspeichers
Es gibt zwei Arten von Einstellungen speichern:  
  
- Konfigurationseinstellungen, die nur-Lese Einstellungen für Visual Studio und das VSPackage. Visual Studio werden die Einstellungen aus allen bekannten PKGDEF-Dateien in diesem Speicher zusammengeführt.  
  
- Benutzereinstellungen, die beschreibbaren Einstellungen wie die, die auf Seiten angezeigt werden, sind die **Optionen** im Dialogfeld Eigenschaftenseiten und bestimmte andere Dialogfelder. Visual Studio-Erweiterungen können diese für die lokale Speicherung von kleine Mengen von Daten verwenden.  
  
  Diese exemplarische Vorgehensweise veranschaulicht das Lesen von Daten aus dem Konfigurationsspeicher für die Einstellung. Finden Sie unter [Schreiben in die Benutzer Einstellungen Store](../extensibility/writing-to-the-user-settings-store.md) eine Erklärung der Vorgehensweise zum Schreiben in den Speicher für benutzereinstellungen.  
  
## <a name="creating-the-example-project"></a>Erstellen das Beispielprojekt  
 In diesem Abschnitt wird gezeigt, wie eine einfache Erweiterung-Projekt mit einem Menübefehl für die Demo erstellt.  
  
1. Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Bereitstellung-Projekt, das die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `SettingsStoreExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2. Fügen Sie jetzt eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **SettingsStoreCommand**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **SettingsStoreCommand.cs**. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Verwenden die Konfiguration Einstellungen Store  
 Dieser Abschnitt beschreibt das Erkennen und Konfigurationseinstellungen anzeigen.  
  
1. Fügen Sie in der Datei SettingsStorageCommand.cs die folgenden using-Anweisungen:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. In `MenuItemCallback`, entfernen Sie den Text der Methode, und fügen Sie diese Zeilen erhalten den Konfigurationsspeicher für die Einstellungen hinzu:  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    Die <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> ist eine verwaltete Hilfsklasse über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Service.  
  
3. Nun herausfinden Sie, ob die Windows Phone-Tools installiert sind. Der Code sollte wie folgt aussehen:  
  
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
  
4. Testen des Codes. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5. In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen SettingsStoreCommand**.  
  
    Daraufhin sollte eine Meldung für das Feld **Microsoft Windows Phone-Entwicklertools:** gefolgt von **"true"** oder **"false"**.  
  
   Visual Studio behält den einstellungsspeicher in der Registrierung des Systems.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Registrierungs-Editor verwenden, um zu überprüfen, ob Konfigurationseinstellungen  
  
1.  Öffnen Sie Regedit.exe.  
  
2.  Navigieren Sie zu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass Sie den Schlüssel anzeigen, die \14.0Exp_Config\ und nicht \14.0_Config enthält\\. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, sind Konfigurationseinstellungen in der Registrierungsstruktur "14.0Exp_Config" ein.  
  
3.  Erweitern Sie den \Installed Products\-Knoten. Wenn die Nachricht in den vorherigen Schritten **Microsoft Windows Phone Developer Tools installiert: "true"**, \Installed Products\ einen Knoten für die Microsoft Windows Phone Developer Tools enthalten soll. Wenn die Nachricht **Microsoft Windows Phone Developer Tools installiert: "false"**, dann \Installed Products\ nicht auf einen Knoten für die Microsoft Windows Phone Developer Tools enthalten soll.