---
title: Einrichten eines Subversion-Repository in Visual Studio für Mac
description: Verwenden von Git und Subversion in Visual Studio für Mac
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: e6b6fd600d3f32c77651b9a4fbb0dff2cd754bcb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="setting-up-a-subversion-repository"></a>Einrichten eines Subversion-Repository

Subversion ist ein zentralisiertes Versionskontrollsystem. Dies bedeutet, dass ein einzelner Server alle Dateien und Reversionen enthält, aus denen Benutzer eine beliebige Version einer beliebigen Datei auschecken können. Wenn Dateien aus einem Remoterepository von Subversion ausgecheckt werden, erhalten Benutzer zu diesem Zeitpunkt eine Momentaufnahme des Repositorys.

Vor der Verwendung von Subversion müssen die Xcode-Befehlszeilentools installiert sein, da sie die richtigen SVN-Pakete enthalten. Sie können im Terminal überprüfen, ob SVN installiert ist, indem sie folgenden Befehl verwenden:

`svn h`

1. Erstellen Sie online ein kostenloses SVN-Repository. In diesem Beispiel wurde [Assembla](https://app.assembla.com/) verwendet. Sobald es erstellt ist, wird eine URL bereitgestellt, die zum Verbinden mit dem Repository verwendet wird: 

    ![Abrufen und Kopieren der SVN-URL](media/version-control-subversion1-sml.png)

2. Öffnen oder erstellen Sie ein Projekt in Visual Studio für Mac.

3. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Version Control > Publish in Version Control...** (Versionskontrolle > In der Versionskontrolle veröffentlichen...): 

    ![Beginnen mit der Veröffentlichung des Projekts](media/version-control-subversion2.png)

4. Klicken Sie in der Registerkarte **Connect to Repository** (Mit Repository verbinden) auf **Subversion** im oberen Dropdownmenü.

5. Geben Sie die URL aus Schritt 1 ein. Dadurch sollten die anderen Felder standardmäßig aufgefüllt werden: 

    ![Auswählen des Repositorys und Dialogfeld „Details eingeben“](media/version-control-subversion3.png)

7. Klicken Sie auf **OK** und bestätigen Sie den Vorgang, indem Sie auf **Publish** (Veröffentlichen) klicken.

7. Sie werden möglicherweise dazu aufgefordert, Ihre Anmeldeinformationen für die Website einzugeben, auf der Sie das Repository erstellen. Geben Sie diese wie unten dargestellt ein:

    ![](media/version-control-subversion5.png)

8.  Alle verfügbaren Befehle der Versionskontrolle sollten nun im Menü „Versionskontrolle“ sichtbar sein.

