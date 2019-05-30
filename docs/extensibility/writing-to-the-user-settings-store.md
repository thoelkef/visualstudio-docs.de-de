---
title: Schreiben in den Store Benutzer Einstellungen | Microsoft-Dokumentation
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44380a03b87318be0fdf746c75eff8988ac68267
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318482"
---
# <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen
Benutzereinstellungen werden beschreibbaren Einstellungen wie die in der **Extras / Optionen** Dialogfeld Eigenschaften von Windows und bestimmte andere Dialogfelder. Visual Studio-Erweiterungen, die diese verwenden können, um kleine Mengen von Daten zu speichern. Diese exemplarische Vorgehensweise veranschaulicht das Editor Visual Studio als externes Tool hinzufügen, indem aus lesen und Schreiben in den Speicher für benutzereinstellungen.

## <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen

1. Erstellen Sie ein VSIX-Projekt mit dem Namen UserSettingsStoreExtension, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen UserSettingsStoreCommand. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

2. UserSettingsStoreCommand.cs, fügen Sie die folgende using-Anweisungen:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. Klicken Sie in MenuItemCallback löschen Sie den Text der Methode, und rufen Sie Benutzer ab, die Einstellungen gespeichert werden, wie folgt:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Nun erfahren Sie, ob der Editor bereits als ein externes Tool eingerichtet ist. In diesem Fall müssen Sie eine Iteration durch alle externen Tools, die bestimmen, ob die Einstellung ToolCmd "Notepad", wie folgt lautet:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Wenn der Editor nicht als ein externes Tool festgelegt wurde, legen Sie es wie folgt:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Testen des Codes. Denken Sie daran, dass sie Editor als externes Tool, hinzufügt, damit Sie die Registrierung wieder zurücksetzen müssen, bevor Sie ihn ein zweites Mal ausführen.

7. Erstellen Sie den Code, und starten Sie das Debuggen.

8. Auf der **Tools** Menü klicken Sie auf **aufrufen UserSettingsStoreCommand**. Dadurch wird hinzugefügt, Editor, um die **Tools** Menü.

9. Editor auf die Tools angezeigt werden soll / Menü, und klicken auf "Optionen" **Editor** sollte eine Instanz von Editor aufzurufen.