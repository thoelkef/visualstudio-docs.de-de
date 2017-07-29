---
title: Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 90e19f6e693733162065754b441fb213fd0bd9f8
ms.contentlocale: de-de
ms.lasthandoff: 07/18/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017
Wenn Sie Visual Studio 2017 von einer Befehlszeile aus installieren, können Sie die verschiedene Befehlszeilenparameter verwenden, um die Installation zu steuern und anzupassen. Sie können über die Befehlszeile Folgendes tun:

- Die Installation mit bestimmten vorab ausgewählten Optionen starten
- Den Installationsprozess automatisieren
- Einen Cache (Layout) der Installationsdateien für den späteren Gebrauch erstellen

Die Befehlszeilenoptionen werden in Verbindung mit dem Setup-Bootstrapper, die kleine Datei (ca. 1 MB), die den Downloadprozess initiiert, verwendet. Der Bootstrapper ist die erste ausführbare Datei, die gestartet wird, wenn Sie von der Visual Studio-Website herunterladen. Sie können einen direkten Link auf den neuesten Release-Bootstrapper für die Produktversion abrufen, die Sie über diese Links installieren:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Liste der Befehlszeilenparameter  
 Bei Visual Studio-Befehlszeilenparametern wird zwischen Groß- und Kleinschreibung nicht unterschieden.

> Syntax: `vs_enterprise.exe [command] <options>...`

(Ersetzen Sie `vs_enterprise.exe` nach Bedarf mit der Produktversion, die Sie installieren) Beispiele finden Sie auf der Seite [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md).)

| **Befehl** | **Beschreibung** |
| ----------------------- | --------------- |
| (leer) | Installiert das Produkt. |
| `modify` | Ändert ein installiertes Produkt. |
| `update` | Aktualisiert ein installiertes Produkt. |
| `repair` | Repariert ein installiertes Produkt. |
| `uninstall` | Deinstalliert ein installiertes Produkt. |

| **Option installieren** | **Beschreibung** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Das Installationsverzeichnis für die Instanz, für die der Befehl ausgeführt wird. Für den Befehl „install“ ist dies **optional** und das Verzeichnis, in dem die Instanz installiert wird. Für andere Befehle ist es **erforderlich** und das Verzeichnis der zuvor installierten Instanz. |
| `--addProductLang <language-locale>` | **Optional**: Während einer Installation oder eines Änderungsvorgang, bestimmt dies die UI-Sprachpakete, die für das Produkt installiert werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Wird diese Option nicht angegeben, verwendet die Installation das Gebietsschema des Computers. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--removeProductLang <language-locale>` | **Optional**: Während einer Installation oder eines Änderungsvorgang, bestimmt dies die UI-Sprachpakete, die vom Produkt entfernt werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <workload or component ID>` | **Optional**: Eine hinzuzufügende Arbeitsauslastung oder Komponenten-ID. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeRecommended;includeOptional`). Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). Sie können dies Option bei Bedarf wiederholen.|
| `--remove <workload or component ID>` | **Optional**: Eine zu entfernende Arbeitsauslastung oder Komponenten-ID. Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). Sie können dies Option bei Bedarf wiederholen.|
| `--in <path>` | **Optional**: Der URI oder Pfad zu einer Antwortdatei.  |
| `--all` | **Optional**: Gibt an, ob alle Arbeitsauslastungen und Komponenten für ein Produkt installiert werden sollen. |
| `--allWorkloads` | **Optional**: Installiert alle Arbeitsauslastungen und deren erforderlichen Komponenten, aber keine empfohlenen oder optionalen Komponenten. |
| `--includeRecommended` | **Optional**: Enthält die empfohlenen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional**: Enthält die optionalen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine empfohlenen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben.  |
| `--quiet, -q` | **Optional**: Während der Installation wird keine Benutzeroberfläche angezeigt. |
| `--passive, -p` | **Optional**: Die Benutzeroberfläche wird angezeigt, es ist aber kein Eingreifen des Benutzers erforderlich. |
| `--norestart` | **Optional**: Wird diese Option angegeben, erfolgt bei Befehlen mit `--passive` oder `--quiet` kein automatischer Neustart des Computers (falls erforderlich). Sie wird ignoriert, wenn weder `--passive` noch `--quiet` angegeben sind.  |
| `--nickname <name>` | **Optional**: Definiert den Spitznamen, der einem installierten Produkt zugewiesen wird. Der Spitzname darf nicht länger als 10 Zeichen sein.  |
| `--productKey` | **Optional**: Legt den Product Key fest, der für ein installiertes Produkt verwendet wird. Er besteht aus 25 alphanumerischen Zeichen im Format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` oder `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Eine Offline-Version dieser Seite wird angezeigt. |

> Hinweis: Wenn Sie mehrere Arbeitsauslastungen und Komponenten angeben, müssen Sie den `--add`- oder `--remove`-Befehlszeilenschalter für jedes Element wiederholen.

| **Layoutoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--layout <dir>` | Gibt ein Verzeichnis an, in dem der Offlineinstallationscache erstellt wird. Weitere Informationen finden Sie unter [Erstellen einer Offlineinstallation von Visual Studio 2017](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Optional**: Wird mit `--layout` zur Vorbereitung eines Offlineinstallationscaches mit Ressourcenpaketen mit angegebenen Sprachen verwendet. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional**: Eine oder mehrere hinzuzufügende Arbeitsauslastungs- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeOptional`). Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). <br/>**Hinweis**: Bei Verwenden von `--add` werden nur die angegebenen Workloads und Komponenten sowie deren Abhängigkeiten heruntergeladen. Wenn `--add` nicht angegeben ist, werden alle Workloads und Komponenten in das Layout heruntergeladen.|
| `--includeRecommended` | **Optional**: Enthält die empfohlenen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional**: Schließt die empfohlenen *und* optionalen Komponenten für alle Workloads in das Layout ein. Die Workloads werden mit `--add` angegeben.  |


| **Erweiterte Installationsoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Optional**: Die ID des Kanals für die Instanz, die installiert wird. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn `--installPath` angegeben ist. |
| `--channelUri <uri>` | **Optional**: Der URI des Kanalmanifests. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installChannelUri <uri>` | **Optional**: Der URI des Kanalmanifests, der für die Installation verwendet werden soll. Der mit `--channelUri` festgelegte URI (der angegeben werden muss, wenn `--installChannelUri` angegeben ist) dient zum Ermitteln von Updates. Werden keine Updates gewünscht, muss `--channelUri` ohne Argument angegeben werden. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installCatalogUri <uri>` | **Optional**: Der URI des Katalogmanifests, der für die Installation verwendet werden soll. Wird diese Option angegeben, versucht der Kanal-Manager, das Katalogmanifest von diesem URI herunterzuladen, bevor der URI im Installationskanalmanifest verwendet wird. Dieser Parameter wird zur Unterstützung der Offlineinstallation verwendet, wobei der Layoutcache mit dem bereits heruntergeladenen Produktkatalog erstellt wird. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--productId <id>` | **Optional**: Die ID des Produkts für die Instanz, die installiert wird. Diese ist bei normalen Installationsbedingungen bereits ausgefüllt. |
| `--wait` | **Optional**: Der Prozess wartet, bis „install“ abgeschlossen ist, bevor er einen Exitcode zurückgibt. Dies ist nützlich beim Automatisieren von Installationen, bei denen auf das Beenden von „install“ gewartet werden muss, um den Rückgabecode von „install“ zu verwenden. |
| `--locale <language-locale>` | **Optional**: Ändert die Anzeigesprache der Benutzeroberfläche für den Installer selbst. Die Einstellung wird beibehalten. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--cache` | **Neu in 15.2 (optional)**: Falls vorhanden, werden Pakete nach ihrer Installation für nachfolgende Reparaturen gespeichert. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--nocache` | **Neu in 15.2 (optional)**: Falls vorhanden, werden Pakete nach ihrer Installation oder Reparatur gelöscht. Sie werden nur bei Bedarf erneut heruntergeladen und nach ihrer Verwendung wieder gelöscht. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |

## <a name="list-of-workload-ids-and-component-ids"></a>Liste der Arbeitsauslastungs-IDs und Komponenten-IDs
Eine Liste der Arbeitsauslastungs- und Komponenten-IDs, sortiert nach Visual Studio-Produkt, finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Liste der Gebietsschemas
| **Gebietsschema** | **Sprache** |
| ----------------------- | --------------- |
| cs-CZ | Tschechisch |
| de-DE | Deutsch |
| en-US | Englisch |
| es-ES | Spanisch |
| fr-FR | Französisch |
| it-IT | Italienisch |
| ja-JP | Japanisch |
| ko-KR | Koreanisch |
| pl-PL | Polnisch |
| pt-BR | Portugiesisch (Brasilien) |
| ru-RU | Russisch |
| tr-TR | Türkisch |
| zh-CN | Chinesisch (vereinfacht) |
| zh-TW | Chinesisch (traditionell) |

## <a name="error-codes"></a>Fehlercodes
Je nach Ergebnis des Vorgangs wird die Umgebungsvariable `%ERRORLEVEL%` auf einen der folgenden Werte festgelegt.

| **Wert** | **Ergebnis** |
| --------- | ---------- |
| 0 | Der Vorgang wurde erfolgreich abgeschlossen. |
| 3010 | Der Vorgang wurde erfolgreich abgeschlossen, für die Installation ist jedoch ein Neustart erforderlich, bevor sie verwendet werden kann. |
| Andere | Es ist ein Fehler aufgetreten – Überprüfen Sie die Protokolle für weitere Informationen |

Jeder Vorgang generiert mehrere Protokolldateien im `%TEMP%`-Verzeichnis, die den Status der Installation angeben. Sortieren Sie die Ordner nach Datum, und suchen Sie Dateien für jeweils den Bootstrapper, die Installer-App und das Setupmodul, die mit `dd_bootstrapper`, `dd_client` und `dd_setup` beginnen.

## <a name="see-also"></a>Siehe auch

 * [Installieren von Visual Studio 2017](install-visual-studio.md)
 * [Erstellen einer Offlineinstallation von Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Beispiele für Befehlszeilenparameter für die Installation von Visual Studio 2017](command-line-parameter-examples.md)
 * [Automatisieren der Visual Studio-Installation mit einer Antwortdatei](automated-installation-with-response-file.md)
 * [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

