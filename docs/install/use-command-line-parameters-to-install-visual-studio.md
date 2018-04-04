---
title: Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/17/2018
ms.reviewer: tims
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 348634224d76b3a7f51246f2be49720173ab8cd3
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017
Wenn Sie Visual Studio 2017 von einer Befehlszeile aus installieren, können Sie die verschiedene Befehlszeilenparameter verwenden, um die Installation zu steuern und anzupassen. Über die Befehlszeile können Sie die folgenden Aktionen durchführen:

- Die Installation mit bestimmten vorab ausgewählten Optionen starten
- Den Installationsprozess automatisieren
- Einen Cache (Layout) der Installationsdateien für den späteren Gebrauch erstellen

Die Befehlszeilenoptionen werden in Verbindung mit dem Setup-Bootstrapper verwendet, die kleine Datei (ca. 1 MB), die den Downloadprozess initiiert. Der Bootstrapper ist die erste ausführbare Datei, die gestartet wird, wenn Sie von der Visual Studio-Website herunterladen. Verwenden Sie die folgenden Links, um einen direkten Link zum neuesten Release-Bootstrapper für die Produktversion zu erhalten, die Sie installieren:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Liste der Befehlszeilenparameter  
 Bei Visual Studio-Befehlszeilenparametern wird zwischen Groß- und Kleinschreibung nicht unterschieden.

> Syntax: `vs_enterprise.exe [command] <options>...`

(Ersetzen Sie `vs_enterprise.exe` nach Bedarf durch die Produktedition, die Sie installieren)

>[!TIP]
> Weitere Informationen zur Verwendung der Befehlszeile für die Installation von Visual Studio 2017 finden Sie auf der Seite mit [Beispielen für Befehlszeilenparameter](command-line-parameter-examples.md).)

| **Befehl** | **Beschreibung** |
| ----------------------- | --------------- |
| (leer) | Installiert das Produkt. |
| `modify` | Ändert ein installiertes Produkt. |
| `update` | Aktualisiert ein installiertes Produkt. |
| `repair` | Repariert ein installiertes Produkt. |
| `uninstall` | Deinstalliert ein installiertes Produkt. |

| **Option installieren** | **Beschreibung** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Das Installationsverzeichnis für die Instanz, für die der Befehl ausgeführt wird. Für den Befehl „install“ ist dies **optional** und das Verzeichnis, in dem die Instanz installiert wird. Für andere Befehle ist es **erforderlich** und befindet sich dort, wo die vorherige Instanz installiert wurde. |
| `--addProductLang <language-locale>` | **Optional**: Während einer Installation oder eines Änderungsvorgang, bestimmt dies die UI-Sprachpakete, die für das Produkt installiert werden. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Wird diese Option nicht angegeben, verwendet die Installation das Gebietsschema des Computers. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--removeProductLang <language-locale>` | **Optional**: Während einer Installation oder eines Änderungsvorgang, bestimmt dies die UI-Sprachpakete, die vom Produkt entfernt werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional**: Eine oder mehrere hinzuzufügende Arbeitsauslastungs- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeRecommended;includeOptional`). Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). Sie können dies Option bei Bedarf wiederholen.|
| `--remove <one or more workload or component IDs>` | **Optional**: Eine oder mehrere zu entfernende Arbeitsauslastungs- oder Komponenten-IDs. Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). Sie können dies Option bei Bedarf wiederholen.|
| `--in <path>` | **Optional**: Der URI oder Pfad zu einer Antwortdatei.  |
| `--all` | **Optional**: Gibt an, ob alle Arbeitsauslastungen und Komponenten für ein Produkt installiert werden sollen. |
| `--allWorkloads` | **Optional**: Installiert alle Arbeitsauslastungen und Komponenten, aber keine empfohlenen oder optionalen Komponenten. |
| `--includeRecommended` | **Optional**: Enthält die empfohlenen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional**: Enthält die optionalen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine empfohlenen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben.  |
| `--quiet, -q` | **Optional**: Während der Installation wird keine Benutzeroberfläche angezeigt. |
| `--passive, -p` | **Optional**: Die Benutzeroberfläche wird angezeigt, es ist aber kein Eingreifen des Benutzers erforderlich. |
| `--norestart` | **Optional**: Wird diese Option angegeben, erfolgt bei Befehlen mit `--passive` oder `--quiet` kein automatischer Neustart des Computers (falls erforderlich).  Sie wird ignoriert, wenn weder `--passive` noch `--quiet` angegeben sind.  |
| `--nickname <name>` | **Optional**: Definiert den Spitznamen, der einem installierten Produkt zugewiesen wird. Der Spitzname darf nicht länger als 10 Zeichen sein.  |
| `--productKey` | **Optional**: Legt den Product Key fest, der für ein installiertes Produkt verwendet wird. Er besteht aus 25 alphanumerischen Zeichen im Format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` oder `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Eine Offline-Version dieser Seite wird angezeigt. |

> Hinweis: Wenn Sie mehrere Arbeitsauslastungen und Komponenten angeben, müssen Sie den `--add`- oder `--remove`-Befehlszeilenwechsel für jedes Element wiederholen.

| **Layoutoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--layout <dir>` | Gibt ein Verzeichnis an, in dem der Offlineinstallationscache erstellt wird. Weitere Informationen finden Sie unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Optional**: Wird mit `--layout` zur Vorbereitung eines Offlineinstallationscaches mit Ressourcenpaketen mit angegebenen Sprachen verwendet. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional**: Eine oder mehrere hinzuzufügende Arbeitsauslastungs- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeOptional`). Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). <br/>**Hinweis**: Bei Verwenden von `--add` werden nur die angegebenen Workloads und Komponenten sowie deren Abhängigkeiten heruntergeladen. Wenn `--add` nicht angegeben ist, werden alle Workloads und Komponenten in das Layout heruntergeladen.|
| `--includeRecommended` | **Optional**: Enthält die empfohlenen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional**: Schließt die empfohlenen *und* optionalen Komponenten für alle Workloads in das Layout ein. Die Workloads werden mit `--add` angegeben.  |
| `--keepLayoutVersion` | **Neu in Version 15.3 (optional)**: Wenden Sie Änderungen auf das Layout an, ohne die Version des Layouts aktualisieren zu müssen. |
| `--verify` | **Neu in Version 15.3 (optional)**: Überprüfen Sie die Inhalte eines Layouts.  Beschädigte oder fehlende Dateien werden aufgelistet. |
| `--fix` | **Neu in Version 15.3 (optional)**: Überprüfen Sie die Inhalte eines Layouts.  Sollten Dateien beschädigt sein oder fehlen, werden sie erneut heruntergeladen.  Für die Korrektur eines Layout ist ein Internetzugriff erforderlich. |
| `--clean <one or more paths to catalogs>` | **Neu in Version 15.3 (optional)**: Entfernt alte Versionen der Komponenten aus einem Layout, das auf eine neuere Version aktualisiert wurde. |

| **Erweiterte Installationsoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Optional**: Die ID des Kanals für die Instanz, die installiert wird. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn `--installPath` angegeben ist. |
| `--channelUri <uri>` | **Optional**: Der URI des Kanalmanifests. Wenn Sie keine Updates wünschen, kann `--channelUri` auf eine nicht vorhandene Datei zeigen. (Z.B. –channelUri C:\doesntExist.chman) Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installChannelUri <uri>` | **Optional**: Der URI des Kanalmanifests, der für die Installation verwendet werden soll. Der mit `--channelUri` festgelegte URI (der angegeben werden muss, wenn `--installChannelUri` angegeben ist) dient zum Ermitteln von Updates. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installCatalogUri <uri>` | **Optional**: Der URI des Katalogmanifests, der für die Installation verwendet werden soll. Wird diese Option angegeben, versucht der Kanal-Manager, das Katalogmanifest von diesem URI herunterzuladen, bevor der URI im Installationskanalmanifest verwendet wird. Dieser Parameter wird zur Unterstützung der Offlineinstallation verwendet, wobei der Layoutcache mit dem bereits heruntergeladenen Produktkatalog erstellt wird. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--productId <id>` | **Optional**: Die ID des Produkts für die Instanz, die installiert wird. Diese ist bei normalen Installationsbedingungen bereits ausgefüllt. |
| `--wait` | **Optional**: Der Prozess wartet, bis die Installation abgeschlossen ist, bevor er einen Exitcode zurückgibt. Dies ist nützlich beim Automatisieren von Installationen, bei denen auf das Beenden von „install“ gewartet werden muss, um den Rückgabecode von „install“ zu verwenden. |
| `--locale <language-locale>` | **Optional**: Ändert die Anzeigesprache der Benutzeroberfläche für den Installer selbst. Die Einstellung wird beibehalten. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--cache` | **Neu in 15.2 (optional)**: Falls vorhanden, werden Pakete nach ihrer Installation für nachfolgende Reparaturen gespeichert. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--nocache` | **Neu in 15.2 (optional)**: Falls vorhanden, werden Pakete nach ihrer Installation oder Reparatur gelöscht. Sie werden nur bei Bedarf erneut heruntergeladen und nach ihrer Verwendung wieder gelöscht. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--noUpdateInstaller` | **Neu in 15.2, optional**: Falls vorhanden, hindert den Installer daran, sich selbst zu aktualisieren, wenn „quiet“ angegeben ist. Der Befehl wird für den Installer einen Fehler auslösen, und der Installer gibt einen Exitcode ungleich 0 (null) zurück, falls „noUpdateInstaller“ mit „quiet“ angegeben wird, wenn ein Installerupdate erforderlich ist. |
| `--noWeb` | **Neu in Version 15.3 (optional)**: Das Setup lädt jetzt jeden Inhalt herunter, der aus dem Internet installiert wird.  Jeder Inhalt, der installiert wird, muss in einem Offlinelayout verfügbar sein.  Wenn dem Layout Inhalt fehlt, schlägt die Einrichtung fehl.  Weitere Informationen finden Sie unter [Deploying from a network installation (Bereitstellung aus einer Netzwerkinstallation)](create-a-network-installation-of-visual-studio.md). |

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
| 1602 | Der Vorgang wurde abgebrochen. |
| 3010 | Der Vorgang wurde erfolgreich abgeschlossen, für die Installation ist jedoch ein Neustart erforderlich, bevor sie verwendet werden kann. |
| 5004 | Der Vorgang wurde abgebrochen. |
| 5007 | Der Vorgang wurde blockiert – der Computer entspricht nicht den Anforderungen. |
| Andere | Es ist ein Fehler aufgetreten – Überprüfen Sie die Protokolle für weitere Informationen |

Jeder Vorgang generiert mehrere Protokolldateien im `%TEMP%`-Verzeichnis, die den Status der Installation angeben. Sortieren Sie die Ordner nach Datum, und suchen Sie Dateien für jeweils den Bootstrapper, die Installer-App und das Setupmodul, die mit `dd_bootstrapper`, `dd_client` und `dd_setup` beginnen.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

 * [Beispiele für Befehlszeilenparameter für die Installation von Visual Studio 2017](command-line-parameter-examples.md)
 * [Erstellen einer Offlineinstallation von Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Automatisieren der Visual Studio-Installation mit einer Antwortdatei](automated-installation-with-response-file.md)
