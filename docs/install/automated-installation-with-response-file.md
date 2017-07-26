---
title: Automatisieren der Visual Studio-Installation mit einer Antwortdatei | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
author: timsneath
ms.author: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: de-de
ms.lasthandoff: 05/11/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>Gewusst wie: Definieren von Einstellungen in einer Antwortdatei
Administratoren, die Visual Studio bereitstellen, können mithilfe des Parameters `--in` eine Antwortdatei angeben, z. B.:

```
vs_enterprise.exe --in customInstall.json
```

Antwortdateien sind [JSON](http://json-schema.org/)-Dateien, deren Inhalt die Befehlszeilenargumente wiedergibt.  Allgemein gilt: Wenn ein Befehlszeilenparameter keine Argumente verwendet (z. B. `--quiet`, `--passive` usw.), muss der Wert in der Antwortdatei TRUE oder FALSE sein.  Wenn er ein Argument verwendet (z. B. `--installPath <dir>`), muss der Wert in der Antwortdatei eine Zeichenfolge sein.  Wenn er ein Argument verwendet und mehrmals in der Befehlszeile vorkommen kann (z. B. `--add <id>`), muss es sich um Array aus Zeichenfolgen handeln.

In der Befehlszeile angegebene Parameter überschreiben Einstellungen in der Antwortdatei, außer im Fall von Parametern, die mehrere Eingaben verwenden (z. B. `--add`), bei denen die in der Befehlszeile angegebenen Eingaben mit den Einstellungen aus der Antwortdatei zusammengeführt werden.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Festlegen einer Standardkonfiguration für Visual Studio

Wenn Sie mit `--layout` einen Cache des Netzwerklayouts erstellt haben, wird im Layout eine anfängliche Datei namens `response.json` erstellt.

Administratoren, die ein Layout erstellen, können die Datei `response.json` im Layout zum Steuern der Standardeinstellungen ändern, die Benutzern angezeigt werden, wenn in die Installation von Visual Studio über das Layout erfolgt.  Wenn ein Administrator beispielsweise bestimmte Workloads und Komponenten für die standardmäßige Installation auswählen möchte, kann der die Datei `response.json` so konfigurieren, dass diese hinzugefügt werden.

Wenn das Visual Studio-Setup aus einem Layoutordner erfolgt, wird die Antwortdatei im Layoutordner _automatisch_ verwendet.  Es ist nicht erforderlich, die Option `--in` zu verwenden.

Sie können die Datei `response.json` aktualisieren, die in einem Offlinelayoutordner erstellt wird, um die Standardeinstellung für Benutzer festzulegen, die die Installation mithilfe dieses Layouts vornehmen. **Es ist jedoch wichtig, dass Sie die vorhandenen Eigenschaften unverändert lassen, die beim Erstellen des Layouts festgelegt wurden.**

Die Basisdatei `response.json` in einem Layout ähnelt dieser bis auf den Wert für das Produkt und den Kanal, das bzw. den Sie installieren:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>Beispiel des Inhalts einer Layoutantwortdatei
Bei diesem Beispiel wird Visual Studio Enterprise mit sechs allgemeinen Workloads und Komponenten mit den Benutzeroberflächensprachen Englisch und Französisch installiert. Sie können dies als Vorlage nutzen, in der sie lediglich die Workloads und Komponenten in diejenigen ändern, die installiert werden sollen.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```
## <a name="see-also"></a>Siehe auch
* [Arbeitsauslastungs- und Komponenten-IDs von Visual Studio 2017](workload-and-component-ids.md)

