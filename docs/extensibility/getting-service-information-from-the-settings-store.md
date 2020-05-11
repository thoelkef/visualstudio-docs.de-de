---
title: Abrufen von Serviceinformationen aus dem Einstellungsspeicher | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711374"
---
# <a name="get-service-information-from-the-settings-store"></a>Abrufen von Serviceinformationen aus dem Einstellungsspeicher
Sie können den Einstellungsspeicher verwenden, um alle verfügbaren Dienste zu finden oder um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.

## <a name="to-list-the-available-services"></a>So listen Sie die verfügbaren Dienste auf

1. Erstellen Sie ein `FindServicesExtension` VSIX-Projekt mit `FindServicesCommand`dem Namen, und fügen Sie dann einen benutzerdefinierten Befehl mit dem Namen hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Fügen Sie in *FindServicesCommand.cs*die folgenden Anweisungen hinzu:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Rufen Sie den Konfigurationseinstellungenspeicher ab, und suchen Sie dann die Unterauflistung mit dem Namen Services. Diese Sammlung umfasst alle verfügbaren Dienste. Entfernen `MenuItemCommand` Sie in der Methode den vorhandenen Code, und ersetzen Sie ihn durch Folgendes:

    ```csharp
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

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

5. Klicken Sie in der experimentellen Instanz im Menü **Extras** auf **FindServicesCommand aufrufen**.

     Es sollte ein Meldungsfeld angezeigt werden, in dem alle Dienste aufgeführt sind.

     Um diese Einstellungen zu überprüfen, können Sie den Registrierungseditor verwenden.

## <a name="find-a-specific-service"></a>Suchen eines bestimmten Dienstes
 Sie können die <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Methode auch verwenden, um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.

1. Suchen Sie im MenuItemCallback des Projekts, das Sie im vorherigen `Services` Verfahren erstellt haben, den Konfigurationseinstellungenspeicher nach der Auflistung, die die von der GUID des Dienstes benannte Unterauflistung enthält. In diesem Fall suchen wir nach dem Hilfedienst.

    ```csharp
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

3. Klicken Sie in der experimentellen Instanz im Menü **Extras** auf **FindServicesCommand aufrufen**.

     Es sollte eine Meldung mit dem Text Help Service Verfügbar angezeigt **werden:** gefolgt von **True** oder **False**. Um diese Einstellung zu überprüfen, können Sie einen Registrierungseditor verwenden, wie in den vorherigen Schritten gezeigt.
