---
title: Konfigurieren von Zielen und Aufgaben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634395"
---
# <a name="configure-targets-and-tasks"></a>Konfigurieren von Zielen und Aufgaben

Sie können MSBuild-Ziele und -Aufgaben so konfigurieren, dass sie prozessextern mit MSBuild ausgeführt werden, damit Sie auf Kontexte abzielen können, die sich von dem unterscheiden, in dem Sie die Ausführung eigentlich vorgesehen haben. Beispielsweise können Sie auf eine 32-Bit-.NET Framework 2.0-Anwendung abzielen, während der Entwicklungscomputer auf einem 64-Bit-.NET Framework 4.5-Betriebssystem ausgeführt wird. Sie können auch auf Computer abzielen die mit .NET Framework 4 oder früher ausgeführt werden. Die Kombination der 32- oder 64-Bitanzahl und der spezifischen .NET Framework-Version wird als der *Zielkontext* bezeichnet.

## <a name="installation"></a>Installation

  Wenn Sie MSBuild von Visual Studio getrennt installieren möchten, können Sie das Installationspaket von der [MSBuild-Downloadsite](https://www.microsoft.com/download/details.aspx?id=40760) herunterladen. Sie müssen außerdem die .NET Framework-Versionen installieren, die Sie verwenden möchten.

## <a name="targets-and-tasks"></a>Ziele und Aufgaben

 MSBuild führt bestimmte Buildaufgaben prozessextern aus, um auf mehr Kontexte abzuzielen.  Beispielsweise kann ein 32-Bit-MSBuild eine Buildaufgabe in einem 64-Bit-Prozess ausführen, um auf einen 64-Bit-Computer abzuzielen. Dies wird durch `UsingTask`-Argumente und `Task`-Parameter gesteuert. Die Ziele, die von .NET Framework 4.5 installiert werden, legen diese Argumente und Parameter fest, und es sind keine Änderungen erforderlich, um Anwendungen für die verschiedenen Zielkontexte zu erstellen.

 Wenn Sie eigene Zielkontext erstellen möchten, müssen Sie diese Argumente und Parameter entsprechend festlegen. In der .NET Framework 4.5-Datei *Microsoft.Common.targets* und in der Datei *Microsoft.Common.Tasks* finden Sie einige Beispiele.  Informationen dazu, wie Sie eine benutzerdefinierte Aufgabe erstellen, die mehrere Zielkontexte verwenden kann, oder wie vorhandene Aufgaben geändert werden, finden Sie unter [Vorgehensweise: Konfigurieren von Zielen und Aufgaben](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Siehe auch

- [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)
