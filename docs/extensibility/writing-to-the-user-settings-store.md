---
title: Schreiben in den Store Benutzer Einstellungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6cfb082e149ef8794d52c011c73e89da17face3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926734"
---
# <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen
Benutzereinstellungen werden beschreibbaren Einstellungen wie die in der **Extras / Optionen** Dialogfeld Eigenschaften von Windows und bestimmte andere Dialogfelder. Visual Studio-Erweiterungen, die diese verwenden können, um kleine Mengen von Daten zu speichern. Diese exemplarische Vorgehensweise veranschaulicht das Editor Visual Studio als externes Tool hinzufügen, indem aus lesen und Schreiben in den Speicher für benutzereinstellungen.  
  
### <a name="backing-up-your-user-settings"></a>Sichern der Benutzereinstellungen  
  
1.  Sie müssen die Einstellungen für externe Tools zurücksetzen, damit Sie debuggen können, und wiederholen Sie den Vorgang sein. Zu diesem Zweck müssen Sie die ursprünglichen Einstellungen speichern, sodass Sie nach Bedarf wiederhergestellt werden können.  
  
2.  Öffnen Sie Regedit.exe.  
  
3.  Navigieren Sie zu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\\.  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass Sie den Schlüssel anzeigen, die \14.0Exp\ und nicht \14.0 enthält\\. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, werden Ihre benutzereinstellungen in der Registrierungsstruktur "14.0Exp" ein.  
  
4.  Mit der rechten Maustaste des \External Tools\-Unterschlüssels, und klicken Sie dann auf **exportieren**. Stellen Sie sicher, dass **ausgewählte Teilstruktur** ausgewählt ist.  
  
5.  Speichern Sie die externen Tools.reg-Ergebnisdatei an.  
  
6.  Später, wenn Sie die Einstellungen für externe Tools zurücksetzen möchten, wählen Sie den Registrierungsschlüssel HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\, und klicken Sie auf **löschen** im Kontextmenü.  
  
7.  Wenn die **Löschen des Schlüssels bestätigen** klicken Sie im angezeigten Dialogfeld **Ja**.  
  
8.  Die externe Tools.reg-Datei, die Sie zuvor gespeichert haben, klicken Sie auf **Öffnen mit**, und klicken Sie dann auf **Registrierungs-Editor**.  
  
## <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen UserSettingsStoreExtension, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen UserSettingsStoreCommand. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  UserSettingsStoreCommand.cs, fügen Sie die folgende using-Anweisungen:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  Klicken Sie in MenuItemCallback löschen Sie den Text der Methode, und rufen Sie Benutzer ab, die Einstellungen gespeichert werden, wie folgt:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Nun erfahren Sie, ob der Editor bereits als ein externes Tool eingerichtet ist. In diesem Fall müssen Sie eine Iteration durch alle externen Tools, die bestimmen, ob die Einstellung ToolCmd "Notepad", wie folgt lautet:  
  
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
  
5.  Wenn der Editor nicht als ein externes Tool festgelegt wurde, legen Sie es wie folgt:  
  
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
  
6.  Testen des Codes. Denken Sie daran, dass sie Editor als externes Tool, hinzufügt, damit Sie die Registrierung wieder zurücksetzen müssen, bevor Sie ihn ein zweites Mal ausführen.  
  
7.  Erstellen Sie den Code, und starten Sie das Debuggen.  
  
8.  Auf der **Tools** Menü klicken Sie auf **aufrufen UserSettingsStoreCommand**. Dadurch wird hinzugefügt, Editor, um die **Tools** Menü.  
  
9. Editor auf die Tools angezeigt werden soll / Menü, und klicken auf "Optionen" **Editor** sollte eine Instanz von Editor aufzurufen.