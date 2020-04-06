---
title: Verwenden des Einstellungsspeichers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698518"
---
# <a name="using-the-settings-store"></a>Verwenden des Einstellungsspeichers
Es gibt zwei Arten von Einstellungen:

- Konfigurationseinstellungen, bei denen es sich um schreibgeschützte Visual Studio- und VSPackage-Einstellungen handelt. Visual Studio führt Einstellungen aus allen bekannten .pkgdef-Dateien in diesem Speicher zusammen.

- Benutzereinstellungen, bei denen es sich um beschreibbare Einstellungen handelt, z. B. die, die auf Seiten im Dialogfeld **Optionen,** Eigenschaftenseiten und bestimmte andere Dialogfelder angezeigt werden. Visual Studio-Erweiterungen können diese für die lokale Speicherung kleiner Datenmengen verwenden.

  In dieser exemplarischen Vorgehensweise wird gezeigt, wie Daten aus dem Konfigurationseinstellungsspeicher gelesen werden. Unter [Schreiben in den Benutzereinstellungsspeicher](../extensibility/writing-to-the-user-settings-store.md) finden Sie eine Erläuterung zum Schreiben in den Benutzereinstellungsspeicher.

## <a name="creating-the-example-project"></a>Erstellen des Beispielprojekts
 In diesem Abschnitt wird gezeigt, wie Sie ein einfaches Erweiterungsprojekt mit einem Menübefehl zur Demonstration erstellen.

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungsprojekt, das die Erweiterungselemente enthält. Erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie ein `SettingsStoreExtension`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt** unter **Visual C- / Erweiterbarkeit**.

2. Fügen Sie nun eine benutzerdefinierte Befehlselementvorlage mit dem Namen **SettingsStoreCommand**hinzu. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C/ Erweiterbarkeit,** und wählen Sie **Benutzerdefinierter Befehl aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in **SettingsStoreCommand.cs**. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Verwenden des Konfigurationseinstellungsspeichers
 In diesem Abschnitt wird gezeigt, wie Konfigurationseinstellungen erkannt und angezeigt werden.

1. Fügen Sie in der Datei SettingsStorageCommand.cs die folgenden Anweisungen hinzu:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. `MenuItemCallback`Entfernen Sie in den Text der Methode, und fügen Sie diese Zeilen hinzu, um den Konfigurationseinstellungenspeicher abzuspeichern:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Der <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> ist eine verwaltete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Hilfsklasse über den Dienst.

3. Finden Sie nun heraus, ob Windows Phone Tools installiert sind. Der Code sollte wie folgt aussehen:

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

4. Testen des Codes Erstellen Sie das Projekt, und starten Sie das Debugging.

5. Klicken Sie in der experimentellen Instanz im Menü **Extras** auf **SettingsStoreCommand aufrufen**.

    Es sollte ein Meldungsfeld mit der Meldung **Microsoft Windows Phone Developer Tools angezeigt werden:** gefolgt von **True** oder **False**.

   Visual Studio speichert die Einstellungen in der Systemregistrierung.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>So verwenden Sie einen Registrierungseditor zum Überprüfen der Konfigurationseinstellungen

1. Öffnen Sie Regedit.exe.

2. Navigieren Sie zu HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-14.0Exp_Config-InstalledProducts\\.

    > [!NOTE]
    > Stellen Sie sicher, dass Sie sich den Schlüssel ansehen, der 14,0Exp_Config" und nicht 14,0_Config\\enthält. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, befinden sich die Konfigurationseinstellungen in der Registrierungsstruktur "14.0Exp_Config".

3. Erweitern Sie den Knoten "Installierte Produkte". Wenn die Meldung in den vorherigen Schritten **Microsoft Windows Phone Developer Tools Installed: True**ist, sollte der Knoten "Installierte Produkte" einen Microsoft Windows Phone Developer Tools-Knoten enthalten. Wenn die Meldung **Microsoft Windows Phone Developer Tools Installed: False**ist, sollte der Knoten "Installierte Produkte" keinen Microsoft Windows Phone Developer Tools-Knoten enthalten.
