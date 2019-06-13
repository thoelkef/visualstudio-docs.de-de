---
title: Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung
titleSuffix: ''
description: Erfahren Sie, wie Sie Visual Studio aktualisieren, und dabei innerhalb einer Baseline für die Wartung bleiben.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 36bbec66e822d7e1daebcadbeeba30e166747368
ms.sourcegitcommit: aeb1a1135dd789551e15aa5124099a5fe3f0f32b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501119"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung

Visual Studio 2019 durchläuft während seines [Produktlebenszyklus](/visualstudio/productinfo/release-rhythm#release-channel-updates) häufige Aktualisierungen. Dies umfasst sowohl Updates für Nebenversionen (z.B.: 16.0 auf 16.1), die neue Features und Komponenten enthalten können, sowie Wartungsupdates (z.B.: 16.0.4 auf 16.0.5), die nur zielgerichtete Korrekturen für kritische Probleme enthalten. 

Unternehmensadministratoren können wählen, ob sie ihre Clients innerhalb einer Baseline für die Wartung halten möchten, die für ein Jahr über die Veröffentlichung der nächsten Baseline für die Wartung hinaus mit Wartungsupdates unterstützt wird. Dies ermöglicht Entwicklern und Administratoren mehr Flexibilität bei der Übernahme der neuen Features, Bugfixes oder Komponenten, die in neuen kleineren Updates enthalten sind. Die erste Baseline für die Wartung ist 16.0.x. Weitere Informationen finden Sie unter [Supportoptionen für Enterprise- und Professional-Kunden](https://docs.microsoft.com/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>So gelangen Sie in eine Baseline für die Wartung

Um mit der Verwendung einer Baseline für die Wartung zu beginnen, laden Sie einen Bootstrapper für eine bestimmte Visual Studio-Installer-Version von [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) herunter. Diese Bootstrapper enthalten Links zu den Produktkonfigurationen, Workloads und Komponenten für diese spezielle Version. 

> [!NOTE]
> Achten Sie darauf, zwischen Bootstrapper für eine bestimmte Version und den normalen Bootstrappern zu unterscheiden. Die normalen Bootstrapper sind so konfiguriert, dass sie jeweils die neueste verfügbare Version von Visual Studio verwenden. Sie enthalten eine Nummer im Dateinamen (z.B. vs_enterprise__123456789-123456789.exe), wenn sie von „my.visualstudio.com“ heruntergeladen werden.

Während der Installation müssen Organisationsadministratoren ihre Clients konfigurieren, um zu verhindern, dass Sie auf die neueste Version aktualisiert werden. Dazu können Sie [die channelUri-Einstellung in der Antwortkonfigurationsdatei ändern](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network), um ein Kanalmanifest im Layout oder lokalen Ordner zu verwenden, [den channelUri-Wert über die Befehlszeile ändern](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet), um eine nicht vorhandene Datei zu verwenden, oder [Richtlinien auf dem Clientsystem festlegen, um durch Deaktivieren der Updates](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating) zu verhindern, dass Clients sich selbst aktualisieren. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Installieren einer Baseline für die Wartung in einem Netzwerk

Für Administratoren, die eine Netzwerklayoutinstallation verwenden, ändern Sie den channelUri-Wert in `response.json` im Layout, um die channelmanifest.json-Datei zu verwenden, die sich im gleichen Ordner befindet. Eine Schritt-für-Schritt-Anleitung finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md). Wenn Sie den channelUri-Wert ändern, können Clients am Layoutspeicherort nach Updates suchen. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Installieren einer Baseline für die Wartung über das Internet

Wenn es sich um eine internetbasierte Installation handelt, fügen Sie `--channelUri` mit einem nicht vorhandenen Kanalmanifest zur Befehlszeile hinzu, die zum Starten des Setups verwendet wird. Dadurch wird verhindert, dass Visual Studio die neueste verfügbare Version für ein Update verwendet. Im Folgenden ein Beispiel:

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Verwenden von Richtlinieneinstellungen, um Clients von der Aktualisierung auszuschließen

Eine weitere Möglichkeit zur Steuerung von Updates auf einem Client besteht darin, [Updatebenachrichtigungen zu deaktivieren](controlling-updates-to-visual-studio-deployments.md). Verwenden Sie diese Option, wenn der channelUri-Wert bei der Installation nicht geändert wurde. Dadurch erhält der Client keine Links zur neuesten verfügbaren Version. Ein Bootstrapper für eine bestimmte Version ist trotzdem erforderlich, um die Aktualisierung auf eine bestimmte Version auf dem Client durchzuführen.

## <a name="how-to-stay-on-a-servicing-baseline"></a>So bleiben Sie in einer Baseline für die Wartung

Ist ein Update für eine Baseline für die Wartung verfügbar, werden über [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) für ein Wartungupdate Bootstrapperdateien für eine bestimmte Version zur Verfügung gestellt. Diese können in verschiedenen Szenarien verwendet werden.

Administratoren, die die Bereitstellung über die Netzwerklayoutinstallation durchführen, sollten den [Layoutspeicherort](update-a-network-installation-of-visual-studio.md) aktualisieren. Clients, die vom Speicherort aus installiert wurden, erhalten Updatebenachrichtigungen. Wenn das Update auf Clients bereitgestellt werden muss, folgen Sie [diesen Anweisungen](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Wenn Sie die Datei „response.json“ für ein Update ändern, fügen Sie keine zusätzlichen Workloads, Komponenten oder Sprachen hinzu. Die Verwaltung dieser Einstellungen muss nach dem Aktualisieren des Produkts als modify-Bereitstellung erfolgen. 

Wenn es sich um eine internetbasierte Installation handelt, führen Sie den neuen Bootstrapper für eine bestimmte Version mit dem Parameter `--channelUri` aus, der auf ein nicht vorhandenes Kanalmanifest auf dem Client verweist. Wenn das Update im stillen oder passiven Modus bereitgestellt wird, verwenden Sie zwei separate Befehle:

1. Aktualisieren Sie zunächst den Visual Studio-Installer: <br>```vs_enterprise.exe --quiet --update```
2. Aktualisieren Sie anschließend die Visual Studio-Anwendung selbst: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Gewusst wie: Definieren von Einstellungen in einer Antwortdatei](automated-installation-with-response-file.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
