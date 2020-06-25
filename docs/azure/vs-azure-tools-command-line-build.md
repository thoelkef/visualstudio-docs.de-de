---
title: Build per Befehlszeile für Azure | Microsoft Docs
description: Build per Befehlszeile für Azure
author: ghogen
manager: jillfra
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: 179737f7a4a55fd6111338363ad6668a43689205
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280764"
---
# <a name="building-azure-projects-from-the-command-line"></a>Erstellen von Azure-Projekten über die Befehlszeile
Mithilfe der Microsoft-Build-Engine (MSBuild) können Sie Produkte in Build-Laborumgebungen erstellen, in denen Visual Studio nicht installiert ist. Von MSBuild wird ein XML-Format für Projektdateien verwendet, das erweiterbar ist und von Microsoft vollständig unterstützt wird. Mit dem MSBuild-Dateiformat können Sie beschreiben, welche Elemente für Plattformen und Konfigurationen erstellt werden müssen.

Sie können MSBuild auch über die Befehlszeile ausführen. Diese Methode wird in diesem Thema beschrieben. Durch Festlegen von Eigenschaften an der Befehlszeile können Sie bestimmte Konfigurationen für ein Projekt erstellen. Entsprechend können Sie die Ziele definieren, die von MSBuild erstellt werden. Weitere Informationen zu Befehlszeilenparametern und MSBuild finden Sie unter [MSBuild-Befehlszeilenreferenz](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>MSBuild-Parameter
Die einfachste Möglichkeit zur Erstellung eines Pakets besteht im Ausführen von MSBuild mit der Option `/t:Publish`. Standardmäßig erstellt dieser Befehl ein Verzeichnis unter dem Stammordner des Projekts, z.B. `<ProjectDirectory>\bin\Configuration\app.publish\`. Beim Erstellen eines Azure-Projekts werden zwei Dateien generiert, die Paketdatei selbst und die zugehörige Konfigurationsdatei:

* Paketdatei (`project.cspkg`)
* Konfigurationsdatei (`ServiceConfiguration.TargetProfile.cscfg`)

In der Standardeinstellung enthält jedes Azure-Projekt eine Dienstkonfigurationsdatei für lokale Builds (Debugging) und eine für Cloudbuilds (Staging oder Produktion). Sie können Dienstkonfigurationsdateien jedoch nach Bedarf hinzufügen oder entfernen. Wenn Sie ein Paket in Visual Studio erstellen, werden Sie gefragt, welche Dienstkonfigurationsdatei für das Paket eingeschlossen werden soll. Beim Erstellen eines Pakets mithilfe von MSBuild ist standardmäßig die lokale Dienstkonfigurationsdatei enthalten. Damit eine andere Dienstkonfigurationsdatei enthalten ist, legen Sie die `TargetProfile`-Eigenschaft des MSBuild-Befehls folgendermaßen fest: `MSBuild /t:Publish /p:TargetProfile=ProfileName`.

Wenn Sie ein alternatives Verzeichnis zur Speicherung des Pakets und der Konfigurationsdateien verwenden möchten, legen Sie den Pfad mithilfe der Option `/p:PublishDir=Directory\` fest, einschließlich des nachgestellten umgekehrten Schrägstrichs als Trennzeichen.

## <a name="next-steps"></a>Nächste Schritte
Nach dem Erstellen des Pakets können Sie es in Azure bereitstellen.