---
title: Schreiben in den Speicher des Benutzers Einstellungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e205fa8850bdd5ee664f66c6d6bb7bf86195bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145411"
---
# <a name="writing-to-the-user-settings-store"></a>Das Schreiben in den Speicher des Benutzers-Einstellungen
Benutzereinstellungen werden beschreibbaren Einstellungen wie den Werten in der **Extras / Optionen** Dialogfeld Eigenschaftenfenstern und bestimmte andere Dialogfelder. Visual Studio-Erweiterungen, die diese verwenden können, um kleine Mengen von Daten zu speichern. In dieser exemplarischen Vorgehensweise zeigt, wie durch Auslesen und Schreiben in den Speicher des Benutzers Einstellungen Editor in Visual Studio als ein externes Tool hinzufügen.  
  
### <a name="backing-up-your-user-settings"></a>Sichern Ihre Benutzereinstellungen  
  
1.  Sie müssen die Einstellungen für externe Tools zurücksetzen, damit Sie debuggen können, und wiederholen Sie den Vorgang sein. Zu diesem Zweck müssen Sie die ursprünglichen Einstellungen speichern, sodass Sie sie nach Bedarf wiederherstellen können.  
  
2.  Öffnen Sie Regedit.exe.  
  
3.  Navigieren Sie zu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\\.  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass Sie den Schlüssel prüfen, die \14.0Exp\ und nicht \14.0 enthält\\. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, werden die benutzereinstellungen in der Registrierungsstruktur "14.0Exp".  
  
4.  Mit der rechten Maustaste des \External Tools\ Unterschlüssels, und klicken Sie dann auf **exportieren**. Stellen Sie sicher, dass **ausgewählte Teilstruktur** ausgewählt ist.  
  
5.  Die resultierende externe Tools.reg-Datei zu speichern.  
  
6.  Später, wenn Sie die externen Tools Einstellungen zurücksetzen möchten, wählen Sie den Registrierungsschlüssel HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\, und klicken Sie auf **löschen** in dem eingeblendeten Kontextmenü.  
  
7.  Wenn die **Schlüssel löschen bestätigen** Dialogfeld angezeigt wird, klicken Sie auf **Ja**.  
  
8.  Mit der rechten Maustaste in der externe Tools.reg-Datei, die Sie zuvor gespeichert haben, klicken Sie auf **Öffnen mit**, und klicken Sie dann auf **Registrierungs-Editor**.  
  
## <a name="writing-to-the-user-settings-store"></a>Das Schreiben in den Speicher des Benutzers-Einstellungen  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen UserSettingsStoreExtension, und fügen Sie einen benutzerdefinierten Befehl mit dem Namen UserSettingsStoreCommand hinzu. Weitere Informationen zur Vorgehensweise beim Erstellen eines benutzerdefinierten Befehls finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  In UserSettingsStoreCommand.cs, fügen Sie die folgenden using-Anweisungen:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  Klicken Sie im MenuItemCallback löschen Sie den Text der Methode, und Abrufen Sie Benutzer, die Einstellungen gespeichert werden, wie folgt:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Nun erfahren Sie, ob der Editor bereits als ein externes Tool eingerichtet ist. Sie müssen die externen Tools zu bestimmen, ob die Einstellung ToolCmd "Editor" wie folgt durchlaufen:  
  
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
  
5.  Wenn Editor nicht als ein externes Tool festgelegt wurde, legen Sie es wie folgt:  
  
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
  
6.  Testen Sie den Code ein. Denken Sie daran, dass er fügt Editor als ein externes Tool hinzu, damit Sie die Registrierung wiederherstellen müssen vor der Ausführung eines zweiten Mal.  
  
7.  Erstellen Sie den Code, und starten Sie das Debuggen.  
  
8.  Auf der **Tools** Menü klicken Sie auf **aufrufen UserSettingsStoreCommand**. Dadurch wird hinzugefügt, Editor, um die **Tools** Menü.  
  
9. Nun Sie Notepad Extras sehen / Optionen im Menü klicken und **Editor** sollte eine Instanz von Editor öffnen.