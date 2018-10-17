---
title: Abrufen von Dienstinformationen aus dem Store-Einstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 485166f6458aafd67a002d9104700c93efc20c15
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189047"
---
# <a name="getting-service-information-from-the-settings-store"></a>Abrufen von Dienstinformationen aus dem Einstellungsspeicher
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den einstellungsspeicher verwenden, um alle verfügbaren Dienste zu finden oder um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.  
  
### <a name="to-list-the-available-services"></a>Die verfügbaren Dienste auflisten  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen FindServicesExtension, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen FindServicesCommand. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  FindServicesCommand.cs, fügen Sie die folgende using-Anweisungen:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Der Konfigurationsspeicher für die Einstellungen zu erhalten, suchen Sie dann die untergeordnete Sammlung benannte Dienste. Diese Sammlung enthält alle verfügbaren Dienste an. Klicken Sie in der Methode MenuItemCommand entfernen Sie den vorhandenen Code, und Ersetzen Sie ihn durch Folgendes:  
  
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
  
5.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen FindServicesCommand**.  
  
     Ein Nachrichtenfeld mit allen Diensten sollte angezeigt werden.  
  
     Um diese Einstellungen zu überprüfen, können Sie den Registrierungs-Editor verwenden.  
  
## <a name="finding-a-specific-service"></a>Suchen nach einem bestimmten Dienst  
 Sie können auch die <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Methode, um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.  
  
1.  Suchen Sie in der MenuItemCallback des Projekts, das Sie im vorherigen Verfahren erstellt haben, den Konfigurationsspeicher für die Einstellungen für die `Services` Sammlung, die die untergeordnete Sammlung mit dem Namen, durch die GUID des Diensts enthält. In diesem Fall sucht es nach den Hilfe-Dienst.  
  
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
  
3.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen FindServicesCommand**.  
  
     Daraufhin sollte eine Meldung mit dem Text **Hilfe-Dienst verfügbar:** gefolgt von **"true"** oder **"false"**. Um diese Einstellung zu überprüfen, können Sie einen Registrierungs-Editor verwenden, wie in den vorherigen Schritten gezeigt.

