---
title: "Abrufen von Dienstinformationen aus dem Speicher-Einstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Abrufen von Dienstinformationen aus dem Speicher-Einstellungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alle verfügbaren Dienste oder um zu bestimmen, ob ein bestimmter Dienst installiert ist, können Sie die Einstellungen speichern verwenden. Sie müssen den Typ der Dienstklasse kennen.  
  
### Die verfügbaren Dienste auflisten  
  
1.  Erstellen Sie ein VSIX\-Projekt mit dem Namen FindServicesExtension, und fügen Sie einen benutzerdefinierten Befehl namens FindServicesCommand hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  FindServicesCommand.cs, fügen Sie folgende using\-Anweisungen:  
  
    ```vb  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
3.  Abrufen der Einstellungen Konfigurationsspeicher, suchen Sie dann die Sammlung mit dem Namen Services. Diese Auflistung enthält alle verfügbaren Dienste. Entfernen Sie in der Methode MenuItemCommand den vorhandenen Code, und Ersetzen Sie ihn durch Folgendes:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string message = "Available services:\n"; IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services"); int n = 0; foreach (string service in collection) { message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n"; } MessageBox.Show(message); }  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
5.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen FindServicesCommand**.  
  
     Daraufhin sollte ein Meldungsfeld Auflisten aller Dienste.  
  
     Um diese Einstellung zu überprüfen, können Sie den Registrierungs\-Editor verwenden.  
  
## Suchen nach einem bestimmten Dienst  
 Sie können auch die <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Methode, um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.  
  
1.  Suchen Sie in der MenuItemCallback des Projekts, das Sie im vorherigen Verfahren erstellt haben, den Konfigurationsspeicher für die Einstellungen für die `Services` Auflistung, die die untergeordnete Sammlung mit dem Namen durch die GUID des Diensts. In diesem Fall suchen wir nach den Hilfe\-Dienst.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper(); bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID); string message = "Help Service Available: " + hasHelpService; MessageBox.Show(message); }  
    ```  
  
2.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
3.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen FindServicesCommand**.  
  
     Daraufhin sollte eine Meldung mit dem Text **Hilfe\-Dienst verfügbar:**  gefolgt von **True** oder **False**. Um diese Einstellung zu überprüfen, können Sie einen Registrierungs\-Editor verwenden, wie in den vorhergehenden Schritten gezeigt.