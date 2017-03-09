---
title: Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/14/2017
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
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 18a3d03663ac96e0751d4a420244b835be7146bf
ms.lasthandoff: 02/22/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017-rc"></a>Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017 RC
Wenn Sie Visual Studio 2017 RC von einer Befehlszeile aus installieren, können Sie die folgenden Befehlszeilenparameter (auch als Schalter bezeichnet) verwenden:  

## <a name="list-of-command-line-parameters"></a>Liste der Befehlszeilenparameter  
 Bei Visual Studio-Befehlszeilenparametern wird nicht zwischen Groß- und Kleinschreibung unterschieden.  

| **Befehlszeilenbefehl** | **Beschreibung** |
| ----------------------- | --------------- |  
| ```modify``` | Ändert ein installiertes Produkt. |
| ```update``` | Aktualisiert ein installiertes Produkt. |
| ```repair``` | Repariert ein installiertes Produkt. |
| ```uninstall``` | Deinstalliert ein installiertes Produkt. |

Wird kein Befehl angegeben, wird das Produkt installiert.

| **Befehlszeilenoption** | **Beschreibung** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | Das Installationsverzeichnis für die Instanz, für die der Befehl ausgeführt wird. Für den Befehl „install“ ist dies das Verzeichnis, in dem die Instanz installiert wird. Für die anderen Befehle ist es das Verzeichnis der zuvor installierten Instanz. |
| ```--productId <id>``` | Die ID des Produkts für die Instanz, die installiert wird. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn „--installPath“ angegeben ist. |
| ```--layout <dir>``` | Optional: Gibt ein Verzeichnis an, in dem der Offlineinstallationscaches erstellt wird. Durch Auswahl dieser Option wird implizit auch die Option „--wait“ hinzugefügt. |
| ```--lang <language-locale>``` *[&#60;Sprachgebietsschema&#62; ...]* | Optional: Ressourcenpakete für Installation/Deinstallation mit den angegebenen Sprachen. |
| ```--add <workload or component ID>``` *[&#60;ID der Arbeitsauslastung oder Komponente&#62; ...]* | Optional: Eine oder mehrere hinzuzufügende Arbeitsauslastungs- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können zusätzliche Komponenten steuern, indem Sie „--includeRecommended“ und/oder „--includeOptional“ global verwenden. Für eine differenziertere Steuerung können Sie „;includeRecommended“ und/oder „;includeOptional“ an die Artefakt-ID anhängen (z.B. „--add Workload1;includeRecommended“ oder „--add Workload2;includeOptional;includeRecommended“). |
| ```--remove <workload or component ID>``` *[&#60;ID der Arbeitsauslastung oder Komponente&#62; ...]* | Optional: Eine oder mehrere zu entfernende Arbeitsauslastungs- oder Komponenten-IDs. |
| ```--all``` | Optional: Gibt an, ob alle Arbeitsauslastungen und Komponenten für ein Produkt installiert werden sollen. |
| ```--allWorkloads``` | Optional: Installiert alle Arbeitsauslastungen und deren erforderliche Komponenten, aber keine empfohlenen oder optionalen Komponenten. |
| ```--includeRecommended``` | Optional: Enthält die empfohlenen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine optionalen Komponenten. Die Arbeitsauslastungen werden entweder mit „--allWorkloads“ oder „--add“ hinzugefügt. |
| ```--includeOptional``` | Optional: Enthält die optionalen Komponenten für alle zu installierenden Arbeitsauslastungen, aber keine empfohlenen Komponenten. Die Arbeitsauslastungen werden entweder mit „--allWorkloads“ oder „--add“ hinzugefügt.  |
| ```--quiet, -q``` | Optional: Während der Installation wird keine Benutzeroberfläche angezeigt. |
| ```--passive, -p``` | Optional: Die Benutzeroberfläche wird angezeigt, es ist aber kein Eingreifen des Benutzers erforderlich. |
| ```--norestart``` | Optional: Wird diese Option angegeben, wird bei Befehlen mit „--passive“ oder „--quiet“ kein automatischer Neustart des Computers ausgeführt (falls erforderlich). Wird ignoriert, wenn weder „--passive“ noch“--quiet“ angegeben sind.  |
| ```--locale <language-locale>``` | Optional: Ändert die Anzeigesprache der Benutzeroberfläche für den Installer. Die Einstellung wird beibehalten. |
| ```--nickname <name>``` | Optional: Definiert den Spitznamen, der einem installierten Produkt zugewiesen wird. Der Spitzname darf nicht länger als 10 Zeichen sein.  |
| ```--help, --?, -h, -?``` | Zeigt die Verwendung der Parameter an. |

>Hinweis: Wenn Sie mehrere Arbeitsauslastungen und Komponenten angeben, müssen Sie den `--add`- oder `--remove`-Befehlszeilenschalter für jedes Element wiederholen.

| **Erweiterte Befehlszeilenoption** | **Beschreibung** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | Optional: Die ID des Kanals für die Instanz, die installiert wird. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn „--installPath“ angegeben ist. |
| ```--channelUri <uri>``` | Optional: Der URI des Kanalmanifests. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| ```--installChannelUri <uri>``` | Optional: Der URI des Kanalmanifests, der für die Installation verwendet werden soll. Der durch „--channelUri“ festgelegte URI (der angegeben werden muss, wenn „--installChannelUri“ angegeben ist) dient zum Ermitteln von Updates. Werden keine Updates gewünscht, muss „--channelUri“ ohne Argument angegeben werden. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| ```--installCatalogUri <uri>``` | Optional: Der URI des Katalogmanifests, der für die Installation verwendet werden soll. Wird diese Option angegeben, versucht der Kanal-Manager, das Katalogmanifest von diesem URI herunterzuladen, bevor der URI im Installationskanalmanifest verwendet wird. Dieser Parameter wird zur Unterstützung der Offlineinstallation verwendet, wobei der Layoutcache mit dem bereits heruntergeladenen Produktkatalog erstellt wird. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| ```--in <path>``` | Optional: Der URI oder Pfad zu einer Antwortdatei.  |
| ```--addProductLang <language-locale>``` | Optional: Definiert die Sprache eines Artefakts (Gruppe, Arbeitsauslastung oder Komponente), das installiert werden soll. Kann mehrmals in der Befehlszeile verwendet werden. Ist für die Befehle „install“ und „modify“ optional und wird für die Befehle „update“, „repair“ und „uninstall“ ignoriert. Wird diese Option nicht angegeben, verwendet die Installation das Gebietsschema des Computers. |
| ```--removeProductLang <language-locale>``` | Optional: Definiert die Sprache eines Artefakts (Gruppe, Arbeitsauslastung oder Komponente), das entfernt werden soll. Kann mehrmals in der Befehlszeile verwendet werden. Ist für die Befehle „install“ und „modify“ optional und wird für die Befehle „update“, „repair“ und „uninstall“ ignoriert. |
| ```--wait``` | Optional: Der Prozess wartet, bis „install“ abgeschlossen ist, bevor er einen Exitcode zurückgibt. Dies ist nützlich beim Automatisieren von Installationen, bei denen auf das Beenden von „install“ gewartet werden muss, um den Rückgabecode von „install“ zu verwenden. |
| ```--productKey``` | Optional: Legt den Product Key fest, der für ein installiertes Produkt verwendet wird. Dieser besteht aus 25 alphanumerischen Zeichen im Format 'xxxxx-xxxxx-xxxxx-xxxxx-xxxxx' oder 'xxxxxxxxxxxxxxxxxxxxxxxxx'. |
## <a name="list-of-workload-ids-and-component-ids"></a>Liste der Arbeitsauslastungs-IDs und Komponenten-IDs
Eine Liste der Arbeitsauslastungs- und Komponenten-IDs, sortiert nach Visual Studio-Produkt, finden Sie auf unserer Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](https://aka.ms/vs2017componentids).

> [!WARNING]
> Der Parameter „--layout“ schlägt fehl, wenn der Setup-.exe-Dateiname Ziffern enthält. Um dieses Problem zu umgehen, müssen Sie die Ziffern aus dem Dateinamen entfernen &mdash; z.B. *vs_community__198521760.1486960229.exe* in ***vs_community.exe*** umbenennen.

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



> [!IMPORTANT]
> Während Visual Studio 2017 RC im Allgemeinen für die Verwendung in einer Produktionsumgebung unterstützt wird, werden die Arbeitsauslastungen und Komponenten, die in der Benutzeroberfläche der Installation als „Vorschau“ gekennzeichnet sind, nicht für die Verwendung in einer Produktionsumgebung unterstützt.

## <a name="see-also"></a>Siehe auch

 * [Installieren von Visual Studio](install-visual-studio.md)
 * [Erstellen einer Offlineinstallation von Visual Studio 2017 RC](create-an-offline-installation-of-visual-studio.md)
 * [Melden eines Problems mit Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

