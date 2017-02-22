---
title: "Das Schreiben in die Benutzereinstellungsspeicher | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# Das Schreiben in die Benutzereinstellungsspeicher
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Benutzer sind beschreibbaren Einstellungen wie in der **Extras \/ Optionen** Dialogfeld Eigenschaften von Windows und bestimmte andere Dialogfelder. Visual Studio\-Erweiterungen können diese verwenden, um kleine Mengen von Daten zu speichern. In dieser exemplarischen Vorgehensweise veranschaulicht, wie Editor in Visual Studio als externes Tool hinzufügen, durch das Lesen und Schreiben in den Speicher des Benutzers Einstellungen.  
  
### Sichern Ihre Benutzer\-Einstellungen  
  
1.  Sie müssen die Einstellungen für externe Tools zurücksetzen, damit Sie debuggen können, und wiederholen Sie den Vorgang sein. Zu diesem Zweck müssen Sie die ursprünglichen Einstellungen speichern, damit Sie sie nach Bedarf wiederherstellen können.  
  
2.  Öffnen Sie Regedit.exe.  
  
3.  Navigieren Sie zu HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\\External Tools\\.  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass Sie den Schlüssel anzeigen, die \\14.0Exp\\ und nicht \\14.0\\ enthält. Wenn Sie die experimentelle Instanz von Visual Studio ausführen, werden Ihre Benutzer in der Registrierungsstruktur "14.0Exp".  
  
4.  Mit der rechten Maustaste des \\External Tools\\ Unterschlüssels, und klicken Sie dann auf **exportieren**. Stellen Sie sicher, dass **Ausgewählte Teilstruktur** ausgewählt ist.  
  
5.  Speichern Sie die resultierende Datei für externe Tools.reg.  
  
6.  Später, wenn Sie die externe Tools Einstellungen zurücksetzen möchten, wählen Sie den Registrierungsschlüssel HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\\External Tools\\, und klicken Sie auf **Löschen** im Kontextmenü.  
  
7.  Wenn die **Löschen des Schlüssels bestätigen** Dialogfeld angezeigt wird, klicken Sie auf **Ja**.  
  
8.  Mit der rechten Maustaste in der externe Tools.reg\-Datei, die Sie zuvor gespeichert haben, klicken Sie auf **Öffnen mit**, und klicken Sie dann auf **Registry Editor**.  
  
## Das Schreiben in die Benutzereinstellungsspeicher  
  
1.  Erstellen Sie ein VSIX\-Projekt mit dem Namen UserSettingsStoreExtension, und fügen Sie einen benutzerdefinierten Befehl namens UserSettingsStoreCommand hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  UserSettingsStoreCommand.cs, fügen Sie folgende using\-Anweisungen:  
  
    ```c#  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback löschen Sie den Text der Methode und erhalten Sie die Benutzer, die Einstellungen gespeichert werden, wie folgt:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings); }  
    ```  
  
4.  Nun erfahren Sie, ob der Editor bereits als externes Tool eingerichtet ist. In diesem Fall müssen Sie eine Iteration durch alle externen Tools zu bestimmen, ob die Einstellung ToolCmd "Editor" wie folgt:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings); // Find out whether Notepad is already an External Tool. int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys"); bool hasNotepad = false; CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo; for (int i = 0; i < toolCount; i++) { if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0) { hasNotepad = true; break; } } }  
  
    ```  
  
5.  Wenn Editor nicht als externes Tool festgelegt wurde, legen Sie es wie folgt:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings); // Find out whether Notepad is already installed. int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys"); bool hasNotepad = false; CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo; for (int i = 0; i < toolCount; i++) { if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0) { hasNotepad = true; break; } } string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad"; if (!hasNotepad) { userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad"); userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe"); userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, ""); userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)"); userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, ""); userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011); userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1); } }  
    ```  
  
6.  Testen Sie den Code. Denken Sie daran fügt Editor als externes Tool, damit Sie die Registrierung wiederherstellen müssen, bevor Sie es ein zweites Mal ausgeführt.  
  
7.  Erstellen Sie den Code, und starten Sie das Debuggen.  
  
8.  Auf der **Tools** Menü klicken Sie auf **aufrufen UserSettingsStoreCommand**. Dadurch wird hinzugefügt, Editor, um die **Tools** Menü.  
  
9. Jetzt Sie Editor auf die Tools sehen \/ Optionen im Menü und auf **Editor** sollte eine Instanz von Editor eingeblendet.