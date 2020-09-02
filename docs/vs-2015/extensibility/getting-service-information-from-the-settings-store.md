---
title: Erhalten von Dienst Informationen aus dem Einstellungs Speicher | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204310"
---
# <a name="getting-service-information-from-the-settings-store"></a>Abrufen von Dienstinformationen aus dem Einstellungsspeicher
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Einstellungs Speicher können Sie alle verfügbaren Dienste suchen oder ermitteln, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.  
  
### <a name="to-list-the-available-services"></a>So Listen Sie die verfügbaren Dienste auf  
  
1. Erstellen Sie ein VSIX-Projekt namens findservicesextension, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen findservicescommand hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) .  
  
2. Fügen Sie in FindServicesCommand.cs die folgenden using-Anweisungen hinzu:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Abrufen des Konfigurations Einstellungs Speicher und suchen der untergeordneten Sammlung mit dem Namen "Dienste". Diese Sammlung enthält alle verfügbaren Dienste. Entfernen Sie in der menuitemcommand-Methode den vorhandenen Code, und ersetzen Sie ihn durch Folgendes:  
  
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
  
4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.  
  
5. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **findservicescommand aufrufen**.  
  
     Es sollte ein Meldungs Feld angezeigt werden, in dem alle Dienste aufgelistet sind.  
  
     Um diese Einstellungen zu überprüfen, können Sie den Registrierungs-Editor verwenden.  
  
## <a name="finding-a-specific-service"></a>Suchen nach einem bestimmten Dienst  
 Sie können auch die- <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Methode verwenden, um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.  
  
1. Suchen Sie im MenuItemCallBack des Projekts, das Sie in der vorherigen Prozedur erstellt haben, im Konfigurations Einstellungs Speicher nach der Auflistung `Services` , die die untergeordnete Sammlung mit dem Namen der GUID des Dienstanbieter aufweist. In diesem Fall suchen wir nach dem Hilfe Dienst.  
  
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
  
2. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
3. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **findservicescommand aufrufen**.  
  
     Es sollte eine Meldung mit dem Text **Help Service**  angezeigt werden: gefolgt von **true** oder **false**. Um diese Einstellung zu überprüfen, können Sie wie in den vorherigen Schritten gezeigt einen Registrierungs-Editor verwenden.
