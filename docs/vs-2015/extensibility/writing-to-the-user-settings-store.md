---
title: Schreiben in den Benutzer Einstellungs Speicher | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841185"
---
# <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Benutzereinstellungen sind beschreibbare Einstellungen wie diejenigen im Dialogfeld Extras **/Optionen** , Eigenschaften Fenster und bestimmte andere Dialogfelder. In Visual Studio-Erweiterungen können diese zum Speichern kleiner Datenmengen verwendet werden. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in Visual Studio Notepad als externes Tool hinzufügen, indem Sie aus dem Benutzer Einstellungs Speicher lesen und darin schreiben.  
  
### <a name="backing-up-your-user-settings"></a>Sichern der Benutzereinstellungen  
  
1. Sie müssen die Einstellungen externer Tools zurücksetzen können, damit Sie das Verfahren Debuggen und wiederholen können. Zu diesem Zweck müssen Sie die ursprünglichen Einstellungen speichern, damit Sie Sie bei Bedarf wiederherstellen können.  
  
2. Öffnen Sie Regedit.exe.  
  
3. Navigieren Sie zu HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0exp\externe Tools \\ .  
  
    > [!NOTE]
    > Stellen Sie sicher, dass Sie den Schlüssel sehen, der \14.0exp\ und Not \ 14,0 enthält \\ . Wenn Sie die experimentelle Instanz von Visual Studio ausführen, befinden sich die Benutzereinstellungen in der Registrierungs Struktur "14,0 Exp".  
  
4. Klicken Sie mit der rechten Maustaste auf den Unterschlüssel \externe Tools \, und klicken Sie dann auf **exportieren**. Stellen Sie sicher, dass **ausgewählter Branch** ausgewählt ist.  
  
5. Speichern Sie die resultierende externe Tools. reg-Datei.  
  
6. Wenn Sie die Einstellungen für externe Tools später zurücksetzen möchten, wählen Sie den HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0exp\externe Tools \-Registrierungsschlüssel aus, und klicken Sie im Kontextmenü auf **Löschen** .  
  
7. Wenn das Dialogfeld **Löschen des Schlüssels bestätigen** angezeigt wird, klicken Sie auf **Ja**.  
  
8. Klicken Sie mit der rechten Maustaste auf die externe Datei Tools. reg, die Sie zuvor gespeichert haben, klicken Sie auf **Öffnen mit**und dann auf **Registrierungs-Editor**.  
  
## <a name="writing-to-the-user-settings-store"></a>Schreiben in den Speicher für Benutzereinstellungen  
  
1. Erstellen Sie ein VSIX-Projekt namens usersettingsstoreextension, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen usersettingsstorecommand hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) .  
  
2. Fügen Sie in UserSettingsStoreCommand.cs die folgenden using-Anweisungen hinzu:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3. Löschen Sie in MenuItemCallBack den Text der-Methode, und rufen Sie den Benutzer Einstellungs Speicher wie folgt ab:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4. Stellen Sie nun fest, ob Notepad bereits als externes Tool festgelegt ist. Sie müssen alle externen Tools durchlaufen, um zu bestimmen, ob die toolcmd-Einstellung wie folgt "Notepad" lautet:  
  
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
  
5. Wenn Notepad nicht als externes Tool festgelegt wurde, legen Sie es wie folgt fest:  
  
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
  
6. Testen des Codes Beachten Sie, dass Sie Notepad als externes Tool hinzufügt, sodass Sie ein Rollback der Registrierung ausführen müssen, bevor Sie ein zweites Mal ausgeführt wird.  
  
7. Erstellen Sie den Code, und starten Sie das Debugging.  
  
8. Klicken Sie **im Menü Extras** auf **usersettingsstorecommand aufrufen**. Dadurch wird Notepad **zum Menü Extras** hinzugefügt.  
  
9. Nun sollte im Menü Extras/Optionen Notepad angezeigt werden, und durch Klicken auf **Notepad** sollte eine Instanz von Notepad angezeigt werden.
