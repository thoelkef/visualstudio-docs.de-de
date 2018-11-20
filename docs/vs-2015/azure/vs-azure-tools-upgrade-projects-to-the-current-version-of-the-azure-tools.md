---
title: 'Gewusst wie: upgrade von Projekten auf die aktuelle Version von Azure Tools | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie ein Azure-Projekt in Visual Studio auf die aktuelle Version von Azure Tools aktualisieren
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c5fb70f2dd09338dd2e2f6b01cb60bf2be0cdbdd
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001987"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Aktualisieren von Projekten auf die aktuelle Version der Azure-Tools für Visual Studio
## <a name="overview"></a>Übersicht
Nach der Installation der aktuellen Version von Azure Tools (oder einer früheren Version, die neuer ist als 1.6), Projekte, die erstellt wurden, mithilfe einer Azure-Tools vor Version 1.6 (November 2011) werden automatisch aktualisiert, sobald Sie sie öffnen. Wenn Sie Projekte mithilfe der 1.6 (November 2011) Version der Tools erstellt haben, und Sie weiterhin diese Version installiert haben, können Sie diese öffnen Sie diese Projekte in der älteren Version und später entscheiden, ob sie aktualisiert.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Wie das Projekt ändert, wenn Sie ein Upgrade durchführen
Wenn ein Projekt automatisch aktualisiert wird, oder Sie angeben, dass Sie sie aktualisieren möchten, das Projekt wird geändert, um mit aktuellen Versionen bestimmter Assemblys fehlerfrei funktioniert, und einige Eigenschaften werden ebenfalls geändert werden, wie in diesem Abschnitt beschrieben. Wenn Ihr Projekt andere Änderungen als kompatibel mit der neueren Version der Tools erforderlich sind, müssen Sie diese Änderungen manuell vornehmen.

* Die Datei "Web.config" für Webrollen und die Datei "App.config" für Workerrollen werden aktualisiert, um auf die neuere Version von "Microsoft.windowsazure.Diagnostics.diagnosticmonitoirtracelistener.dll" einzufügen zu verweisen.
* Die Assemblys Microsoft.WindowsAzure.StorageClient.dll Microsoft.WindowsAzure.Diagnostics.dll und "Microsoft.windowsazure.ServiceRuntime.dll" werden auf die neuen Versionen aktualisiert.
* Veröffentlichungsprofile, die in der azure_projektdatei (ccproj-Format) gespeichert wurden in einer separaten Datei mit der azurepubxml-Erweiterung verschoben werden in der **veröffentlichen** Unterverzeichnis.
* Einige Eigenschaften im Veröffentlichungsprofil werden aktualisiert, um neue und geänderte Funktionen zu unterstützen. **AllowUpgrade** Fassung **DeploymentReplacementMethod** da bereitgestellte Cloud-Dienste simultan oder inkrementell aktualisiert werden können.
* Die Eigenschaft **UseIISExpressByDefault** wurde hinzugefügt und auf "false" festgelegt werden, sodass der Webserver, der für das Debuggen nicht automatisch von Internet Information Services (IIS) für IIS Express geändert. IIS Express ist der Standardwebserver für Projekte, die mit den neueren Versionen der Tools erstellt werden.
* Wenn Azure Caching in einer oder mehreren Ihres Projekts Rollen gehostet wird, werden einige Eigenschaften in der Dienstkonfiguration (cscfg-Datei) und die Dienstdefinition (csdef-Datei) geändert, wenn ein Projekt aktualisiert wird. Wenn das Projekt über das Azure-Caching NuGet-Paket verwendet, wird das Projekt auf die neueste Version des Pakets aktualisiert. Öffnen Sie die Datei "Web.config", und stellen Sie sicher, dass die Clientkonfiguration während des Upgradevorgangs ordnungsgemäß beibehalten wurde. Diese Assemblys wird nicht aktualisiert werden, wenn Sie die Verweise auf Azure Cache-Clientassemblys ohne das NuGet-Paket hinzugefügt haben, Sie müssen diese Verweise auf die neuen Versionen manuell aktualisieren.

> [!IMPORTANT]
> Für F# -Projekten müssen Sie Verweise auf Assemblys von Azure manuell aktualisieren, sodass sie die neueren Versionen dieser Assemblys verweisen.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Wie Sie ein Azure-Projekt auf die aktuelle Version aktualisieren
1. Installieren Sie die aktuelle Version der Azure-Tools in der Installation von Visual Studio, die Sie für das aktualisierte Projekt verwenden möchten, und öffnen Sie das Projekt, das Sie aktualisieren möchten. Wenn es sich bei der Erstellung des Projekts mit einer Azure Tools vor Version 1.6 (November 2011), das Projekt automatisch auf die aktuelle Version aktualisiert. Wenn das Projekt erstellt wurde mit der November 2011 release dieser Version ist weiterhin installiert und das Projekt wird geöffnet, in dieser Version.
2. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für den Projektknoten, und wählen **Eigenschaften**, und wählen Sie dann die **Anwendung** Registerkarte des Dialogfelds, das angezeigt wird.
   
    Die **Anwendung** Registerkarte zeigt die Tools-Version, die dem Projekt zugeordnet ist. Wenn die aktuelle Version der Azure-Tools angezeigt wird, wurde das Projekt bereits aktualisiert. Wenn Sie über eine neuere Version der Tools als auf der Registerkarte angezeigt wird, installiert haben, eine **Upgrade** Schaltfläche angezeigt wird.
3. Wählen Sie die **Upgrade** Schaltfläche, um ein Projekt auf die aktuelle Version der Tools aktualisieren.
4. Erstellen Sie das Projekt, und beheben Sie Fehler, die von API-Änderungen ergeben. Informationen dazu, wie Sie Ihren Code für die neue Version ändern finden Sie in der Dokumentation zur jeweiligen API.

