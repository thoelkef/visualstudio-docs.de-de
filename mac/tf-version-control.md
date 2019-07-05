---
title: Team Foundation-Versionskontrolle (TFVC)
description: Herstellen einer Verbindung zwischen Visual Studio für Mac und Team Foundation Server/Azure DevOps mit der Team Foundation-Versionskontrolle (TFVC)
author: conceptdev
ms.author: crdun
ms.date: 06/25/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 04a251621af1086c15bafa15b7a9fe01f8dab5a8
ms.sourcegitcommit: 9d3529e40438ca45dcb0b31742c4cd5a89daa61e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398980"
---
# <a name="connecting-to-team-foundation-version-control"></a>Herstellen einer Verbindung mit der Team Foundation-Versionskontrolle

> [!NOTE]
> Für die beste Versionskontrolle unter macOS empfehlen wir die Verwendung von Git anstelle von Team Foundation Version Control (TFVC). Git wird in Visual Studio für Mac unterstützt und ist die Standardoption für Repositorys, die in Team Foundation Server (TFS)/Azure DevOps gehostet werden. Weitere Informationen zur Verwendung von Git mit TFS/Azure DevOps finden Sie im Artikel [Einrichten eines Git-Repository](/visualstudio/mac/set-up-git-repository).
> 
> Wenn Sie zuvor die Vorschauversion der TFVC-Erweiterung für Visual Studio für Mac verwendet haben: Diese wird in Visual Studio 2019 für Mac nicht mehr unterstützt.

Azure Repos bietet zwei Modelle der Versionskontrolle: [Git](/azure/devops/repos/git/?view=azure-devops), ein verteiltes Versionskontrollsystem oder ein zentralisiertes Versionskontrollsystem mit [Team Foundation-Versionskontrolle](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC).

Visual Studio für Mac bietet volle Unterstützung für Git-Repositorys, erfordert aber einige Workarounds, um mit TFVC zu arbeiten. Wenn Sie heute TFVC für die Versionskontrolle verwenden, finden Sie hier einige Lösungen, mit denen Sie auf Ihren in TFVC gehosteten Quellcode zugreifen können:

* [Verwenden von Visual Studio Code und der Azure Repos-Erweiterung für eine grafische Benutzeroberfläche](#use-visual-studio-code-and-the-azure-repos-extension)
* [Verbinden mit Ihrem Repository über den Team Explorer Everywhere Command Line Client (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

Der Rest dieses Artikels führt Sie durch die oben aufgeführten Optionen.

## <a name="requirements"></a>Requirements (Anforderungen)

* Visual Studio Community, Professional oder Enterprise für Mac 7.8 und höher
* Azure DevOps Services, Team Foundation Server 2013 und höher oder Azure DevOps Server 2018 und höher
* Ein Projekt in Azure DevOps Services oder Team Foundation Server/Azure DevOps Server, das für die Verwendung der Team Foundation-Versionskontrolle konfiguriert ist.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Verwenden von Visual Studio Code und der Azure Repos-Erweiterung

Wenn Sie mit einer grafischen Oberfläche arbeiten möchten, um Ihre Dateien in der Versionskontrolle zu verwalten, dann bietet die Azure Repos-Erweiterung für Visual Studio Code eine unterstützte Lösung von Microsoft. Um zu beginnen, laden Sie [Visual Studio Code](https://code.visualstudio.com) herunter, und erfahren Sie dann, wie Sie [die Azure Repos-Erweiterung konfigurieren](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Verbinden über den Team Explorer Everywhere Command Line Client

Wenn Sie mit der Verwendung des macOS-Terminals vertraut sind, bietet der Team Explorer Everywhere Command Line Client (TEE-CLC) eine unterstützte Möglichkeit, sich mit Ihrer Quelle in TFVC zu verbinden.

Sie können die folgenden Schritte ausführen, um Ihre Verbindung zu TFVC einzurichten und Änderungen zu committen.

### <a name="setting-up-the-tee-clc"></a>Einrichten des TEE-CLC

Es gibt zwei Möglichkeiten, einen TEE-CLC einzurichten.

* Verwenden von Homebrew, um den Client installieren oder
* Herunterladen und den Client manuell zu installieren

Die einfachste Lösung ist **HomeBrew**, ein Paket-Manager für macOS. So führen Sie die Installation mit dieser Methode aus:

1. Starten Sie die MacOS-Terminal-Anwendung.
1. Installieren Sie Homebrew mit dem Terminal und den Anweisungen auf der [Homebrew-Homepage](https://brew.sh/).
1. Sobald Homebrew installiert ist, führen Sie den folgenden Befehl über Ihr Terminal aus: `brew install tee-clc`

So **richten Sie TEE-CLC manuell ein**:

1. [Laden Sie die neueste Version des TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) von Seite zum Release von Team Explorer Everywhere--GitHub-Repository herunter (z.B. tee-clc-14.134.0.0.zip zum Zeitpunkt der Erstellung dieses Artikels).
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner auf Ihrem Datenträger.
1. Öffnen Sie die macOS-Terminal-App und wechseln Sie mit dem Befehl `cd` zu dem Ordner, den Sie im vorherigen Schritt verwendet haben.
1. Führen Sie innerhalb des Ordners den Befehl `./tf` aus, um zu testen, ob der CLS ausgeführt werden kann. Sie werden möglicherweise aufgefordert, Java oder andere Abhängigkeiten zu installieren.

Sobald die TEE-CLC installiert ist, können Sie den Befehl `tf eula` ausführen, um die Lizenzvereinbarung für den Client anzuzeigen und anzunehmen.

Um sich mit Ihrer TFS/Azure DevOps-Umgebung zu authentifizieren, müssen Sie schließlich einen persönlichen Zugriffstoken auf dem Server erstellen. Erfahren Sie mehr über [Authentifizierung mit persönlichen Zugriffstoken](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Wenn Sie ein persönliches Zugriffstoken für TFVC erstellen, stellen Sie sicher, dass Sie bei der Konfiguration des Token vollen Zugriff haben.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Verwenden des TEE-CLC zum Verbinden mit Ihrem Repository

Um eine Verbindung zu Ihrem Quellcode herzustellen, müssen Sie zunächst mit dem Befehl `tf workspace` einen Arbeitsbereich erstellen. Die folgenden Befehle stellen beispielsweise einen Verbindung mit einer Organisation in Azure DevOps Services namens „MyOrganization“ her: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Die Umgebungseinstellung `TF_AUTO_SAVE_CREDENTIALS` wird verwendet, um Ihre Anmeldeinformationen zu speichern, damit Sie sie nicht mehrmals eingeben müssen. Wenn Sie nach einem Benutzernamen gefragt werden, verwenden Sie den persönlichen Zugangscode, den Sie im vorherigen Abschnitt erstellt haben, und verwenden Sie ein leeres Kennwort.

Um eine Zuordnung Ihrer Quelldateien zu einem lokalen Ordner zu erstellen, verwenden Sie den Befehl `tf workfold`. Das folgende Beispiel bildet einen Ordner namens „WebApp.Services“ aus dem TFVC-Projekt „MyRepository“ ab und richtet ihn so ein, dass er in den lokalen Ordner ~/Projekte/ kopiert wird (d.h. einen Ordner „Projects“ im Ausgangsordner des aktuellen Benutzers).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Abschließend verwenden Sie den folgenden Befehl, um die Quelldateien vom Server abzurufen und lokal zu kopieren:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Committen von Änderungen mithilfe des TEE-CLC

Nachdem Sie Änderungen an Ihren Dateien in Visual Studio für Mac vorgenommen haben, können Sie zum Terminal zurückkehren, um Ihre Änderungen einzuchecken. Der Befehl `tf add` wird verwendet, um Dateien zur Liste der ausstehenden Änderungen hinzuzufügen, die eingecheckt werden sollen, und der Befehl `tf checkin` führt das eigentliche Einchecken auf dem Server durch. Der Befehl `checkin` enthält Parameter, um einen Kommentar hinzuzufügen oder einem zugehörigen Arbeitselement zuzuordnen. Im folgenden Codeausschnitt werden alle Dateien in einem `WebApp.Services` Ordner rekursiv zum Einchecken hinzugefügt. Anschließend wird der Code mit einem Kommentar eingecheckt und einem Arbeitselement mit der ID „42“ zugeordnet.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Um mehr über die hier genannten oder andere Befehle zu erfahren, können Sie den folgenden Befehl aus dem Terminal verwenden:

`tf help`

### <a name="see-also"></a>Siehe auch

- [Entwickeln und Freigeben von Code in TFVC mit Visual Studio (unter Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)