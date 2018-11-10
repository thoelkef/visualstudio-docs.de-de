---
title: Konfigurieren Ihres Azure-Projekts mit mehreren Dienstkonfigurationen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Azure-Cloud-Service-Projekt zu konfigurieren, indem Sie die Dateien "Servicedefinition.csdef" ServiceConfiguration.Local.cscfg und ServiceConfiguration.Cloud.cscfg ändern.
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f309c2a960d011601a9fdd41e29d767c667de838
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002002"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurieren Ihres Azure-Projekts in Visual Studio zur Verwendung mehrerer Dienstkonfigurationen

Ein Azure-Cloud-Dienstprojekt in Visual Studio enthält drei Konfigurationsdateien: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`, und `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` in Azure, die zum Beschreiben der Anforderungen von Cloud-Diensts und seiner Rollen, und um Einstellungen bereitzustellen, die für alle Instanzen gelten bereitgestellt wird. Einstellungen können zur Laufzeit mithilfe der Azure Service Hosting Runtime-API gelesen werden. Diese Datei kann in Azure aktualisiert werden, nur, wenn der Clouddienst beendet wird.
- `ServiceConfiguration.Local.cscfg` und `ServiceConfiguration.Cloud.cscfg` Geben Sie Werte für Einstellungen in der Definition der Datei, und geben Sie die Anzahl der für jede Rolle auszuführenden Instanzen. "Local"-Datei enthält Werte, die beim lokalen Debuggen verwendet. die Datei "Cloud" wird bereitgestellt, in Azure als `ServiceConfiguration.cscfg` und bietet Einstellungen für die serverumgebung. Diese Datei kann aktualisiert werden, während Sie Ihren Clouddienst in Azure ausgeführt wird.

Konfigurationseinstellungen verwaltet und in Visual Studio mithilfe von Eigenschaftenseiten für die jeweilige Rolle geändert werden (mit der rechten Maustaste in der Rolle, und wählen Sie **Eigenschaften**, oder doppelklicken Sie auf die Rolle ""). Änderungen in die Konfiguration ausgewählt ist begrenzt werden die **Dienstkonfiguration** Dropdownliste aus. Die Eigenschaften für Web- und workerrolle sind ähnlich, außer wenn in den folgenden Abschnitten beschrieben.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Weitere Informationen zu den zugrunde liegenden Schemas für die Dienstdefinition und die Dienstkonfigurationsdateien finden Sie unter den [csdef-Datei XML-Schema](/azure/cloud-services/schema-csdef-file.md) und [.cscfg-XML-Schema](/azure/cloud-services/schema-cscfg-file.md) Artikel. Weitere Informationen zur Dienstkonfiguration finden Sie unter [Konfigurieren von Clouddiensten wie](/azure/cloud-services/cloud-services-how-to-configure-portal).


## <a name="configuration-page"></a>Seite "Konfiguration"

### <a name="service-configuration"></a>Dienstkonfiguration

Wählt die `ServiceConfiguration.*.cscfg` Datei von Änderungen betroffen ist. Standardmäßig lokale und Cloud-Varianten vorhanden sind, und Sie können die **verwalten...**  Befehl zu kopieren, umbenennen und Konfigurationsdateien entfernen. Diese Dateien werden Ihrem clouddienstprojekt hinzugefügt und werden in **Projektmappen-Explorer**. Allerdings kann das Umbenennen oder Entfernen von Konfigurationen nur über dieses Steuerelement erfolgen.

### <a name="instances"></a>Instanzen

Legen Sie die **Instanz** count-Eigenschaft, um die Anzahl der Instanzen, die der Dienst für diese Rolle ausführen soll.

Legen Sie die **VM-Größe** Eigenschaft **sehr klein**, **kleine**, **Mittel**, **groß**, oder **Extragroßen**.  Weitere Informationen finden Sie unter [Größen für Clouddienste](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Startaktion (nur Webrolle)

Legen Sie diese Eigenschaft angeben, dass das Starten von Visual Studio sollte eines Webbrowsers für den HTTP-Endpunkten oder das HTTPS-Endpunkte oder beides beim Starten des Debuggens.

Die **HTTPS-Endpunkt** Option ist nur verfügbar, wenn Sie bereits einen HTTPS-Endpunkt für Ihre Rolle definiert haben. Sie können einen HTTPS-Endpunkt definieren, auf die **Endpunkte** Eigenschaftenseite.

Wenn Sie bereits einen HTTPS-Endpunkt hinzugefügt haben, ist die Option "HTTPS-Endpunkt" standardmäßig aktiviert, und Visual Studio startet einen Browser für diesen Endpunkt aus, wenn der start des Debugvorgangs zusätzlich zum Browser für den HTTP-Endpunkt, vorausgesetzt, dass beide Startoptionen aktiviert sind.

### <a name="diagnostics"></a>Diagnose

Standardmäßig sind die Diagnose für die Webrolle aktiviert. Das Azure-Cloud-Projekt und Speicher-Dienstkonto werden festgelegt, um den lokalen Speicheremulator verwenden. Wenn Sie zum Bereitstellen in Azure bereit sind, können Sie auswählen, dass die generatorschaltfläche (**...** ) zu Azure-Speicher verwenden. Sie können die Diagnose-Daten bei Bedarf oder in automatisch geplanten Intervallen an das Speicherkonto übertragen. Weitere Informationen zur Azure-Diagnose finden Sie unter [Aktivieren der Diagnose in Azure Cloud Services und Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Seite "Einstellungen"

Auf der **Einstellungen** Seite Sie können einer Konfiguration Einstellungen als Name / Wert-Paare hinzufügen. In dieser Rolle ausgeführtem Code kann die Werte der Konfigurationseinstellungen zur Laufzeit anhand von Klassen ausgelesen der [verwaltete Azure-Bibliothek](http://go.microsoft.com/fwlink?LinkID=171026), insbesondere die [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) Methode.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurieren einer Verbindungszeichenfolge für ein Speicherkonto

Eine Verbindungszeichenfolge ist eine Einstellung, die Verbindungs- und Authentifizierungsinformationen für den Speicheremulator oder für Azure Storage-Konto enthält. Wenn Code in einer Azure-Speicher (Blobs, Warteschlangen oder Tabellen) zugreift, benötigt sie eine Verbindungszeichenfolge an.

> [!Note]
> Verwenden Sie eine Verbindungszeichenfolge für Azure Storage-Konto muss ein definiertes Format aufweisen (finden Sie unter [Konfigurieren von Azure Storage-Verbindungszeichenfolgen](/azure/storage/common/storage-configure-connection-string)).

Sie können der Verbindungszeichenfolge für lokalen Speicher verwendet, legen Sie dann auf Azure Storage-Konto bei der Bereitstellung der Anwendung benötigt werden, den Cloud-Dienst festlegen. Fehler bei die Verbindungszeichenfolge richtig festgelegt wird möglicherweise Ihre Rolle nicht gestartet, oder die initialisieren, ausgelastet und wird beendet-Status zu durchlaufen.

Wählen Sie zum Erstellen einer Verbindungszeichenfolge **Einstellung hinzufügen** und **Typ** auf "Verbindungszeichenfolge".

Wählen Sie für neue oder vorhandene Verbindungszeichenfolgen **...** * rechts neben der **Wert** zu öffnen der **Verbindungszeichenfolge für Speicherkonto** Dialogfeld:

1. Klicken Sie unter **Herstellen einer Verbindung mit**, wählen Sie die **Ihres Abonnements** Option aus, um ein Speicherkonto aus einem Abonnement auszuwählen. Visual Studio ruft dann die Anmeldeinformationen des Speicherkontos automatisch aus der `.publishsettings` Datei.
1. Auswählen von **manuell eingegebene Anmeldeinformationen** können Sie den Kontonamen angeben und den Schlüssel direkt mithilfe von Informationen aus dem Azure-Portal. Um den kontoschlüssel zu kopieren:
    1. Navigieren Sie zu dem Speicherkonto auf Azure-Portal und wählen **Schlüssel verwalten**.
    1. Navigieren Sie zum Speicherkonto im Azure-Portal, wählen, um den kontoschlüssel zu kopieren, **Einstellungen > Zugriffsschlüssel**, klicken Sie dann verwenden Sie die Schaltfläche "Kopieren", um den primären Zugriffsschlüssel in die Zwischenablage zu kopieren.
1. Wählen Sie eine der Verbindungsoptionen. **Benutzerdefinierte Endpunkte angeben** werden Sie aufgefordert, das Angeben von bestimmten URLs für Blobs, Tabellen und Warteschlangen. Benutzerdefinierte Endpunkte ermöglichen Ihnen die Verwendung [benutzerdefinierte Domänen](/azure/storage/blobs/storage-custom-domain-name.md) und den Zugriff genauer steuern. Finden Sie unter [Konfigurieren von Azure Storage-Verbindungszeichenfolgen](/azure/storage/common/storage-configure-connection-string).
1. Wählen Sie **OK**, klicken Sie dann **Datei > Speichern** um die Konfiguration durch die neue Verbindungszeichenfolge zu aktualisieren.

Wenn Sie Ihre Anwendung in Azure veröffentlichen, wählen Sie in diesem Fall die Dienstkonfiguration, die Azure Storage-Konto für die Verbindungszeichenfolge enthält. Nachdem die Anwendung veröffentlicht wurde, stellen Sie sicher, dass die Anwendung funktioniert, mit der Azure-Speicherdiensten wie erwartet.

Weitere Informationen über das Aktualisieren von Dienstkonfigurationen finden Sie im Abschnitt [Verwalten von Verbindungszeichenfolgen für Speicherkonten](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Seite "Endpunkte"

Eine Webrolle weist normalerweise einen einzelnen HTTP-Endpunkt an Port 80 an. Eine workerrolle haben dagegen auf eine beliebige Anzahl von HTTP, HTTPS oder TCP-Endpunkten. Endpunkte können sein, instanzeingabe-Endpunkten, die für externe Clients verfügbar sind, oder interne Endpunkte, die für andere Rollen verfügbar sind, die im Dienst ausgeführt werden.

- Ändern Sie den Typ des Endpunkts für die Eingabe, und geben Sie einen Namen und eine öffentliche Portnummer, um einen HTTP-Endpunkt für externe Clients und Webbrowser verfügbar zu machen.
- Um einen HTTPS-Endpunkt für externe Clients und Webbrowser verfügbar zu machen, ändern Sie den Endpunkttyp in **Eingabe**, und geben Sie einen Namen, eine öffentliche Portnummer und Namen eines verwaltungszertifikats. Außerdem müssen Sie das Zertifikat definieren, auf die **Zertifikate** Eigenschaftenseite, bevor Sie ein Verwaltungszertifikat angeben können. 
- Um einen Endpunkt von anderen Rollen im Cloud-Dienst für den internen Zugriff verfügbar zu machen, ändern Sie den Endpunkttyp auf interne, und geben Sie einen Namen und mögliche private Ports für diesen Endpunkt.

## <a name="local-storage-page"></a>Seite "Lokaler Speicher"

Sie können die **lokalen Speicher** Eigenschaftenseite, um eine oder mehrere lokale Speicherressourcen für eine Rolle zu reservieren. Eine lokale Speicherressource ist ein reserviertes Verzeichnis im Dateisystem des virtuellen Azure-Computer in dem eine Instanz einer Rolle ausgeführt wird.

## <a name="certificates-page"></a>Seite "Zertifikate"

Die **Zertifikate** Eigenschaftenseite der Dienstkonfiguration Informationen zu den Zertifikaten hinzugefügt. Beachten Sie, dass Ihre Zertifikate nicht mit dem Dienst paketiert werden. Sie müssen Ihre Zertifikate separat Hochladen in Azure über die [Azure-Portal](http://portal.azure.com).

Hinzufügen eines Zertifikats Hier werden der Dienstkonfiguration Informationen zu den Zertifikaten hinzugefügt. Zertifikate werden nicht mit dem Dienst verpackt; Sie müssen Ihre Zertifikate separat über das Azure-Portal hochladen.

Geben Sie einen Namen für das Zertifikat, um Ihre Rolle ein Zertifikat zuzuordnen. Verwenden Sie diesen Namen, um auf das Zertifikat zu verweisen, beim Konfigurieren eines HTTPS-Endpunkts auf die **Endpunkte** Seite. Geben Sie als Nächstes, ob der Zertifikatspeicher ist **lokalen Computer** oder **Aktueller Benutzer** und den Namen des Speichers. Geben Sie schließlich den Fingerabdruck des Zertifikats. Wenn das Zertifikat in Current User\Personal (My) Speicher ist, können Sie den Fingerabdruck des Zertifikats eingeben, indem Sie das Zertifikat aus einer aufgefüllten Liste auswählen. Wenn sie an einem anderen Standort befindet, geben Sie den Fingerabdruckwert manuell ein.

Wenn Sie ein Zertifikat aus dem Zertifikatspeicher hinzufügen, werden alle Zwischenzertifikate die Konfigurationseinstellungen für Sie automatisch hinzugefügt. Darüber hinaus müssen diese Zwischenzertifikate in Azure, um Ihr Dienst ordnungsgemäß für SSL konfigurieren hochgeladen werden.

Alle Verwaltungszertifikate, die Sie dem Dienst zugeordneten gelten für den Dienst, nur, wenn sie in der Cloud ausgeführt wird. Wenn der Dienst in der lokalen Entwicklungsumgebung ausgeführt wird, wird ein Standardzertifikat verwendet, das vom Serveremulator verwaltet wird.
