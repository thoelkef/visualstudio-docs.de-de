---
title: Build per Befehlszeile für Azure | Microsoft-Dokumentation
description: Build per Befehlszeile für Azure
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002005"
---
# <a name="building-azure-projects-from-the-command-line"></a>Erstellen von Azure-Projekte über die Befehlszeile
Verwenden die Microsoft Build Engine (MSBuild), können Sie Produkte in Build-laborumgebungen erstellen, dem Visual Studio nicht installiert ist. MSBuild verwendet eine XML-Format für Projektdateien, die erweiterbar und von Microsoft vollständig unterstützt. Mit dem MSBuild-Dateiformat, Sie können beschreiben, welche Elemente sein müssen für eine oder mehrere Plattformen und Konfigurationen erstellt.

Sie können MSBuild auch an der Befehlszeile ausführen, und diese Methode wird in diesem Thema beschrieben. Durch Festlegen von Eigenschaften in der Befehlszeile angegeben, können Sie bestimmte Konfigurationen für ein Projekt erstellen. Auf ähnliche Weise können Sie auch die Ziele definieren, die MSBuild erstellt werden. Weitere Informationen zu Befehlszeilenparametern und MSBuild finden Sie unter [MSBuild-Befehlszeilenreferenz](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>MSBuild-Parameter
Die einfachste Möglichkeit zum Erstellen eines Pakets ist die Ausführung von MSBuild mit der `/t:Publish` Option. Standardmäßig erstellt dieser Befehl ein Verzeichnis unter dem Stammordner des Projekts, wie z. B. `<ProjectDirectory>\bin\Configuration\app.publish\`. Wenn Sie ein Azure-Projekt erstellen, werden zwei Dateien generiert: die Paketdatei selbst und die zugehörige Konfigurationsdatei:

* Paketdatei (`project.cspkg`)
* Konfigurationsdatei (`ServiceConfiguration.TargetProfile.cscfg`)

In der Standardeinstellung enthält jedes Azure-Projekt eine Dienstkonfigurationsdatei für lokale (Debugging-) Builds und eine für cloudbuilds (Staging oder Produktion). Allerdings können Sie hinzufügen oder entfernen Dienstkonfigurationsdateien aus, je nach Bedarf. Wenn Sie ein Paket in Visual Studio erstellen, werden Sie gefragt, welche Dienstkonfigurationsdatei zusammen mit das Paket eingeschlossen werden. Wenn Sie ein Paket mithilfe von MSBuild erstellen, ist die lokale Dienstkonfigurationsdatei standardmäßig enthalten. Wenn eine andere Dienstkonfigurationsdatei einschließen möchten, legen die `TargetProfile` Eigenschaft des MSBuild-Befehls (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Wenn Sie ein alternatives Verzeichnis für die Speicherung des Pakets und der Konfigurationsdateien verwenden möchten, legen Sie den Pfad mithilfe der `/p:PublishDir=Directory\` auswählen, einschließlich des nachgestellten umgekehrten Schrägstrich-Trennzeichen.

## <a name="next-steps"></a>Nächste Schritte
Nachdem das Paket erstellt wurde, können Sie es in Azure bereitstellen.