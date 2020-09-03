---
title: Verwenden von Befehlszeilen Parametern zum Installieren von Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180250"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [Verwenden von Befehlszeilen Parametern zum Installieren von Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Wenn Sie Visual Studio 2015 von einer Eingabeaufforderung aus installieren, können Sie die folgenden Befehlszeilenparameter (auch als Schalter bezeichnet) verwenden.

> [!NOTE]
> Stellen Sie sicher, dass Sie das eigentliche Installationsprogramm und nicht die Bootstrapperdatei verwenden. Stellen Sie z. b. sicher, dass Sie **`vs_enterprise.exe`** anstelle von vs_enterprise_*GUID*. exe verwenden. Sie können ein Installationsprogramm von [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)herunterladen.

## <a name="list-of-command-line-parameters"></a>Liste der Befehlszeilenparameter

Bei Visual Studio-Befehlszeilenparametern wird nicht zwischen Groß- und Kleinschreibung unterschieden.

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/h**|Zeigt die Befehlszeilenparameter an.|
|**/AddRemoveFeatures**|Gibt an, welche Funktionen vom installierten Produkt entfernt oder zu diesem hinzugefügt werden.|
|**/AdminFile** *AdminDeployment.xml*|Installiert Visual Studio mithilfe der von Ihnen für administrative Installation angegebenen Datendatei.|
|**/ChainingPackage** *bundlename*|Gibt an, welches Bündel dieses Bündel verkettet. Dies kann auch zum Angeben einer Customer Improvement Experience-Gruppe verwendet werden.|
|**/CreateAdminFile \<filename>**|Gibt den Speicherort an, um eine Kontrolldateien zu erstellen, die mit „/AdminFile“ verwendet werden kann.|
|**/CustomInstallPath** *InstallationDirectory*|Installiert alle alternativen Pakete in dem von Ihnen angegebenen Verzeichnis.|
|**/ForceRestart**|Startet den Computer nach der Installation immer neu.|
|**/full**|Installiert alle Produktfunktionen.|
|**/InstallSelectableItems \<item name 1> [; \<item name 2> ]**|Liste der Auswahlstrukturelemente, die auf dem Auswahlbildschirm des Installations-Assistenten aktiviert werden sollen.|
|**/l**<br /><br /> **/Log** *Dateiname*|Gibt einen Speicherort für die Protokolldatei an.|
|**/Layout** *Verzeichnis*|Kopiert die Dateien auf dem Installationsmedium in das von Ihnen angegebene Verzeichnis.|
|**/NoCacheOnlyMode**|Verhindert, dass der Paket-Cache vorab gefüllt wird.|
|**/NoRefresh**|Verhindert die Überprüfung auf neuere erforderliche oder empfohlene Versionen dieses Produkts.|
|**/norestart**|Hindert die Installationsanwendung während oder nach der Installation am Neustart des Computers. Informationen zu den Rückgabecodes, nach denen Sie suchen müssen, finden Sie im [Administratorhandbuch für Visual Studio](../install/visual-studio-administrator-guide.md) im Abschnitt „Rückgabecodes“.|
|**/noweb**|Verhindert Installation aus dem Internet.|
|**/OverrideFeedUri \<path to feed file>**|Pfad zu einem lokalen, externen Feed mit einer Beschreibung der Softwareelemente.|
|**/ProductKey**<br /><br /> *ProductKey*|Legt einen benutzerdefinierten Product Key fest, der keine Bindestriche und nicht mehr als 25 Zeichen enthält.|
|**/PromptRestart**|Fordert vor Neustart des Computers den Benutzer auf.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|Unterdrückt die Benutzeroberfläche (UI) für die Installationsanwendung. Wenn Visual Studio bereits installiert ist und Sie keine weiteren Parameter angeben, wird die Installationsanwendung in Wartungsmodus ausgeführt.|
|**/qb**<br /><br /> **/passive**|Zeigt den Fortschritt an, erwartet jedoch keine Benutzereingaben.|
|**/repair**|Repariert Visual Studio.|
|**/SuppressRefreshPrompt**|Verhindert die Anzeige des Dialogfeld über verfügbare Updates im Installations-Assistenten. Der Installations-Assistent nimmt automatisch alle erforderlichen und empfohlenen aktualisierten Versionen an.|
|**/u**<br /><br /> **/Uninstall**|Deinstalliert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/Uninstall/Force**<br /><br /> **/u /force**|Deinstalliert Visual Studio und alle Funktionen, die mit anderen Produkten gemeinsam genutzt werden. **Warnung:**  Wenn Sie diesen Parameter verwenden, funktionieren andere Produkte, die auf dem gleichen Computer installiert sind, möglicherweise nicht mehr ordnungsgemäß.|

## <a name="see-also"></a>Weitere Informationen

- [Administrator Handbuch für Visual Studio](../install/visual-studio-administrator-guide.md)