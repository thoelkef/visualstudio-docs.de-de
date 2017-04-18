---
title: Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
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
translationtype: Human Translation
ms.sourcegitcommit: 2a6555eb9c0a88b1533428cf2aa932b3fc4960ec
ms.openlocfilehash: e8ddcebccc5a8a949c75a33de6732d42134e6445
ms.lasthandoff: 03/30/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017
Wenn Sie Visual Studio 2017 von einer Befehlszeile aus installieren, können Sie die verschiedene Befehlszeilenparameter verwenden, um die Installation zu steuern und anzupassen. Sie können von der Befehlszeile aus Folgendes tun:
- Die Installation mit bestimmten vorab ausgewählten starten 
- Den Installationsprozess automatisieren
- Einen Cache (Layout) der Installationsdateien für den späteren Gebrauch erstellen 

Die Befehlszeilenoptionen werden in Verbindung mit dem Setup-Bootstrapper, die kleine Datei (ca. 1 MB), die den Downloadprozess initiiert, verwendet. Der Bootstrapper ist die erste ausführbare Datei, die gestartet wird, wenn Sie von der Visual Studio-Website herunterladen. Sie können einen direkten Link auf den neuesten Release-Bootstrapper für die Produktversion abrufen, die Sie über diese Links installieren:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Liste der Befehlszeilenparameter  
 Bei Visual Studio-Befehlszeilenparametern wird zwischen Groß- und Kleinschreibung nicht unterschieden.

>  Syntax: `vs_enterprise.exe [command] <options>...`

(ersetzen Sie `vs_enterprise.exe` nach Bedarf mit der Produktversion, die Sie installieren)

| **Befehl** | **Beschreibung** |
| ----------------------- | --------------- | 
| (leer) | Installiert das Produkt. | 
| ```modify``` | Ändert ein installiertes Produkt. |
| ```update``` | Aktualisiert ein installiertes Produkt. |
| ```repair``` | Repariert ein installiertes Produkt. |
| ```uninstall``` | Deinstalliert ein installiertes Produkt. |


| **Option installieren** | **Beschreibung** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | Das Installationsverzeichnis für die Instanz, für die der Befehl ausgeführt wird. Für den Befehl „install“ ist dies das Verzeichnis, in dem die Instanz installiert wird. Für die anderen Befehle ist es das Verzeichnis der zuvor installierten Instanz. |
| ```--layout <dir>``` | **Optional**: Gibt ein Verzeichnis an, in dem der Offlineinstallationscache erstellt wird. Durch Auswahl dieser Option wird implizit auch die Option „--wait“ hinzugefügt. Wenn er aus einer Batchdatei aufgerufen wird, wird dieser Befehl abgeschlossen, bevor die Ausführung an den nächsten Befehl in der Batchdatei übergeben wird. |
| ```--lang <language-locale>``` *[&#60;Sprachgebietsschema&#62; ...]* | **Optional**: Wird mit „--layout“ zur Vorbereitung eines Offline-Installationscaches mit Ressourcenpaketen mit der angegebenen Sprache (bzw. den Sprachen) verwendet. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| ```--addProductLang <language-locale>``` | **Optional**: Während einer Installation oder eines Änderungsvorgang, bestimmt dies die UI-Sprachpakete, die für das Produkt installiert werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Wird diese Option nicht angegeben, verwendet die Installation das Gebietsschema des Computers. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| ```--removeProductLang <language-locale>``` | **Optional**: Während einer Installation oder eines Änderungsvorgang, bestimmt dies die UI-Sprachpakete, die vom Produkt entfernt werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| ```--add <workload or component ID>``` *[&#60;ID der Arbeitsauslastung oder Komponente&#62; ...]* | **Optional**: Eine oder mehrere hinzuzufügende Arbeitsauslastungs- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können zusätzliche Komponenten steuern, indem Sie „--includeRecommended“ und/oder „--includeOptional“ global verwenden. Für eine differenziertere Steuerung können Sie „;includeRecommended“ und/oder „;includeOptional“ an die Artefakt-ID anhängen (z.B. „--add Workload1;includeRecommended“ oder „--add Workload2;includeOptional;includeRecommended“). Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017).|
| ```--remove <workload or component ID>``` *[&#60;ID der Arbeitsauslastung oder Komponente&#62; ...]* | **Optional**: Eine oder mehrere zu entfernende Arbeitsauslastungs- oder Komponenten-IDs. Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017).|
| ```--in <path>``` | **Optional**: Der URI oder Pfad zu einer Antwortdatei.  |
| ```--all``` | **Optional**: Gibt an, ob alle Arbeitsauslastungen und Komponenten für ein Produkt installiert werden sollen. |
| ```--allWorkloads``` | **Optional**: Installiert alle Arbeitsauslastungen und deren erforderlichen Komponenten, aber keine empfohlenen oder optionalen Komponenten. |
| ```--includeRecommended``` | **Optional**: Enthält die empfohlenen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine optionalen Komponenten. Die Arbeitsauslastungen werden entweder mit „--allWorkloads“ oder „--add“ hinzugefügt. |
| ```--includeOptional``` | **Optional**: Enthält die optionalen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine empfohlenen Komponenten. Die Arbeitsauslastungen werden entweder mit „--allWorkloads“ oder „--add“ hinzugefügt.  |
| ```--quiet, -q``` | **Optional**: Während der Installation wird keine Benutzeroberfläche angezeigt. |
| ```--passive, -p``` | **Optional**: Die Benutzeroberfläche wird angezeigt, es ist aber kein Eingreifen des Benutzers erforderlich. |
| ```--norestart``` | **Optional**: Wird diese Option angegeben, wird bei Befehlen mit „--passive“ oder „--quiet“ kein automatischer Neustart des Computers ausgeführt (falls erforderlich). Wird ignoriert, wenn weder „--passive“ noch“--quiet“ angegeben sind.  |
| ```--nickname <name>``` | **Optional**: Definiert den Spitznamen, der einem installierten Produkt zugewiesen wird. Der Spitzname darf nicht länger als 10 Zeichen sein.  |
| ```--productKey``` | **Optional**: Legt den Product Key fest, der für ein installiertes Produkt verwendet wird. Dieser besteht aus 25 alphanumerischen Zeichen im Format 'xxxxx-xxxxx-xxxxx-xxxxx-xxxxx' oder 'xxxxxxxxxxxxxxxxxxxxxxxxx'. |
| ```--help, --?, -h, -?``` | Eine Offline-Version dieser Seite wird angezeigt. |

> Hinweis: Wenn Sie mehrere Arbeitsauslastungen und Komponenten angeben, müssen Sie den `--add`- oder `--remove`-Befehlszeilenschalter für jedes Element wiederholen.

| **Erweiterte Installationsoptionen** | **Beschreibung** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | **Optional**: Die ID des Kanals für die Instanz, die installiert wird. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn „--installPath“ angegeben ist. |
| ```--channelUri <uri>``` | **Optional**: Der URI des Kanalmanifests. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| ```--installChannelUri <uri>``` | **Optional**: Der URI des Kanalmanifests, der für die Installation verwendet werden soll. Der durch „--channelUri“ festgelegte URI (der angegeben werden muss, wenn „--installChannelUri“ angegeben ist) dient zum Ermitteln von Updates. Werden keine Updates gewünscht, muss „--channelUri“ ohne Argument angegeben werden. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| ```--installCatalogUri <uri>``` | **Optional**: Der URI des Katalogmanifests, der für die Installation verwendet werden soll. Wird diese Option angegeben, versucht der Kanal-Manager, das Katalogmanifest von diesem URI herunterzuladen, bevor der URI im Installationskanalmanifest verwendet wird. Dieser Parameter wird zur Unterstützung der Offlineinstallation verwendet, wobei der Layoutcache mit dem bereits heruntergeladenen Produktkatalog erstellt wird. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| ```--productId <id>``` | Die ID des Produkts für die Instanz, die installiert wird. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn „--installPath“ angegeben ist. |
| ```--wait``` | **Optional**: Der Prozess wartet, bis „install“ abgeschlossen ist, bevor er einen Exitcode zurückgibt. Dies ist nützlich beim Automatisieren von Installationen, bei denen auf das Beenden von „install“ gewartet werden muss, um den Rückgabecode von „install“ zu verwenden. |
| ```--locale <language-locale>``` | **Optional**: Ändert die Anzeigesprache der Benutzeroberfläche für den Installer selbst. Die Einstellung wird beibehalten. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|

## <a name="list-of-workload-ids-and-component-ids"></a>Liste der Arbeitsauslastungs-IDs und Komponenten-IDs
Eine Liste der Arbeitsauslastungs- und Komponenten-IDs, sortiert nach Visual Studio-Produkt, finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Liste der Gebietsschemas
| **Gebietsschema** | **Sprache** |
| ----------------------- | --------------- |  
| cs-CZ | Tschechisch |
| de-DE | Deutsch |
| en-US | Englisch |
| es-ES | Spanisch |
| cs-CZ | Tschechisch |
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

 * [Installieren von Visual Studio](install-visual-studio.md)
 * [Erstellen einer Offlineinstallation von Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Melden eines Problems mit Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

