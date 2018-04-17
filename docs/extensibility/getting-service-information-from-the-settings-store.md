---
title: Abrufen von Dienstinformationen aus dem Store Einstellungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11731e36517ae6245dddd1ebdd3b002fb3c37391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="getting-service-information-from-the-settings-store"></a>Die Informationen abrufen aus dem Einstellungen Store
Alle verfügbaren Dienste suchen oder um zu bestimmen, ob ein bestimmter Dienst installiert ist, können Sie den Store Einstellungen verwenden. Sie müssen den Typ der Dienstklasse kennen.  
  
### <a name="to-list-the-available-services"></a>Die verfügbaren Dienste auflisten  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen FindServicesExtension, und fügen Sie einen benutzerdefinierten Befehl mit dem Namen FindServicesCommand hinzu. Weitere Informationen zur Vorgehensweise beim Erstellen eines benutzerdefinierten Befehls finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  In FindServicesCommand.cs, fügen Sie die folgenden using-Anweisungen:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Der Konfigurationsspeicher Einstellungen erhalten, suchen Sie dann die untergeordnete Sammlung mit dem Namen Services. Diese Auflistung enthält alle verfügbaren Dienste an. Klicken Sie in der MenuItemCommand-Methode entfernen Sie den vorhandenen Code, und Ersetzen Sie es durch Folgendes:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
5.  In der experimentellen Instanz auf dem **Tools** Menü klicken Sie auf **aufrufen FindServicesCommand**.  
  
     Daraufhin sollte ein Meldungsfeld Auflisten aller Dienste.  
  
     Um diese Einstellungen zu überprüfen, können Sie den Registrierungs-Editor verwenden.  
  
## <a name="finding-a-specific-service"></a>Suchen nach einem bestimmten Dienst  
 Sie können auch die <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Methode, um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.  
  
1.  Suchen Sie in der MenuItemCallback des Projekts, die Sie im vorherigen Verfahren erstellt haben, den Konfigurationsspeicher für die Einstellungen für die `Services` -Auflistung, die die untergeordnete Sammlung, die durch die GUID des Diensts benannt wurde. In diesem Fall sehen wir für den Hilfe-Dienst.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
3.  In der experimentellen Instanz auf dem **Tools** Menü klicken Sie auf **aufrufen FindServicesCommand**.  
  
     Daraufhin sollte eine Meldung mit dem Text **Hilfe Dienst verfügbar:** gefolgt von **"true"** oder **"false"**. Um diese Einstellung zu überprüfen, können Sie einen Registrierungs-Editor verwenden, wie in den vorherigen Schritten gezeigt.