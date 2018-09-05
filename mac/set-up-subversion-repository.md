---
title: Einrichten eines Subversion-Repositorys
description: Verwenden Subversion in Visual Studio für Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: 8e8e17f7787486e5f14fd94927278bb957439e81
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224221"
---
# <a name="setting-up-a-subversion-repository"></a>Einrichten eines Subversion-Repository

Subversion ist ein zentralisiertes _Versionskontrollsystem_, was bedeutet, dass ein einzelner Server alle Dateien und Revisionen enthält, aus denen Benutzer eine beliebige Version einer beliebigen Datei auschecken können. Wenn Dateien aus einem Remoterepository von Subversion ausgecheckt werden, erhalten Benutzer eine Momentaufnahme des Repositorys.

Sie müssen Subversion auf Ihrem Computer installieren, damit Sie dieses System zur Versionskontrolle verwenden können. Verwenden Sie den folgenden Befehl im Terminal, wenn Sie überprüfen möchten, ob Subversion bereits auf Ihrem Computer installiert wurde:

```bash
svn --version
```

Dieser Befehl gibt die Versionsnummer zurück.

Wenn Subversion noch nicht installiert wurde, installieren Sie am besten die _Xcode-Befehlszeilentools_. Verwenden Sie den nachfolgenden Code, um die Xcode-Befehlszeilentools und Subversion zu installieren.

```bash
xcode-select --install
```

Sobald Sie Subversion auf Ihrem Computer installiert haben, führen Sie die folgenden Schritte aus, um Ihr Projekt in SVN zu veröffentlichen.

1. Erstellen Sie online ein kostenloses SVN-Repository. In diesem Beispiel wurde [Assembla](https://app.assembla.com/) verwendet. Sobald es erstellt ist, wird eine URL bereitgestellt, die zum Verbinden mit dem Repository verwendet wird: 

    ![Die SVN-URL kopieren](media/version-control-subversion1-sml.png)

2. Öffnen oder erstellen Sie ein Projekt in Visual Studio für Mac.

3. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Version Control > Publish in Version Control...** (Versionskontrolle > In der Versionskontrolle veröffentlichen...): 

    ![Beginnen mit der Veröffentlichung des Projekts](media/version-control-subversion2.png)

4. Klicken Sie in der Registerkarte **Mit Repository verbinden** im oberen Dropdownmenü auf **Subversion**.

5. Geben Sie die URL aus Schritt 1 ein. Sobald Sie die URL eingegeben haben, werden die anderen Felder standardmäßig aufgefüllt: 

    ![Auswählen des Repositorys und Dialogfeld „Details eingeben“](media/version-control-subversion3.png)

7. Klicken Sie auf **OK** und bestätigen Sie den Vorgang, indem Sie auf **Publish** (Veröffentlichen) klicken.

7. Geben Sie, sofern Sie dazu aufgefordert werden, wie in der folgenden Abbildung dargestellt Ihre Anmeldeinformationen für die Website ein, auf der Sie das Repository erstellen:

    ![Anmeldeinformationen für das Subversion-Repository eingeben](media/version-control-subversion5.png)

8.  Alle verfügbaren Befehle der Versionskontrolle sollten nun im Menü „Versionskontrolle“ sichtbar sein.

