---
title: Erhalten von Dienst Informationen aus dem Einstellungs Speicher | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51aa0369793fe5dc4b39fe510c069a7ec93d102a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647980"
---
# <a name="get-service-information-from-the-settings-store"></a>Dienst Informationen aus dem Einstellungs Speicher
Mit dem Einstellungs Speicher können Sie alle verfügbaren Dienste suchen oder ermitteln, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.

## <a name="to-list-the-available-services"></a>So Listen Sie die verfügbaren Dienste auf

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `FindServicesExtension`, und fügen Sie dann den benutzerdefinierten Befehl `FindServicesCommand` hinzu. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) .

2. Fügen Sie in *FindServicesCommand.cs*die folgenden using-Direktiven hinzu:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Abrufen des Konfigurations Einstellungs Speicher und suchen der untergeordneten Sammlung mit dem Namen "Dienste". Diese Sammlung enthält alle verfügbaren Dienste. Entfernen Sie in der `MenuItemCommand`-Methode den vorhandenen Code, und ersetzen Sie ihn durch Folgendes:

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

5. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **findservicescommand aufrufen**.

     Es sollte ein Meldungs Feld angezeigt werden, in dem alle Dienste aufgelistet sind.

     Um diese Einstellungen zu überprüfen, können Sie den Registrierungs-Editor verwenden.

## <a name="find-a-specific-service"></a>Suchen eines bestimmten Dienstanbieter
 Sie können auch die <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A>-Methode verwenden, um zu bestimmen, ob ein bestimmter Dienst installiert ist. Sie müssen den Typ der Dienstklasse kennen.

1. Suchen Sie im MenuItemCallBack-Element des Projekts, das Sie in der vorherigen Prozedur erstellt haben, im Konfigurations Einstellungs Speicher nach der `Services`-Sammlung, die die untergeordnete Sammlung mit der GUID des-Dienstanbieter aufweist. In diesem Fall suchen wir nach dem Hilfe Dienst.

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

3. Klicken Sie **in der experimentellen Instanz im Menü Extras** auf **findservicescommand aufrufen**.

     Es sollte eine Meldung mit dem Text **Help Service** angezeigt werden: gefolgt von **true** oder **false**. Um diese Einstellung zu überprüfen, können Sie wie in den vorherigen Schritten gezeigt einen Registrierungs-Editor verwenden.
