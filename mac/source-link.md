---
title: Debuggen in NuGet-Paketen mithilfe von SourceLink
description: In diesem Artikel wird das SourceLink-Feature in Visual Studio für Mac beschrieben.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583917"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debuggen in NuGet-Paketen mithilfe von SourceLink

Die SourceLink-Technologie ermöglicht das Debuggen von Quellcode von .NET-Assemblys aus NuGet, die .PDBs mit Links zu Quelldateien ausliefern. SourceLink wird ausgeführt, wenn Entwickler ihr NuGet-Paket erstellen und Metadaten der Quellcodeverwaltung in Assemblys und in das Paket einbetten. Wenn SourceLink in Visual Studio für Mac aktiviert ist, erkennt die IDE, ob Quelldateien für installierte Pakete verfügbar sind. Visual Studio für Mac bietet dann an, sie herunterzuladen, wodurch Sie den Paketcode schrittweise durchlaufen können. SourceLink funktioniert auch mit dem Code der Mono Base Class Library für Xamarin-Projekte, sodass Sie auch in den Code von .NET Framework springen können. SourceLink bietet Metadaten zur Quellcodeverwaltung, um das Debuggen zu optimieren.

> [!NOTE]
> Visual Studio für Mac unterstützt derzeit keine Symbolserver. Aus diesem Grund wird SourceLink mit Metadaten, die auf Symbolservern gehostet werden, nicht unterstützt.

## <a name="enable-source-link"></a>Aktivieren von SourceLink

Um SourceLink in Visual Studio für Mac zu aktivieren, wechseln Sie zu **Visual Studio > Preferences... > Projects > Debugger** (Visual Studio > Voreinstellungen > Projekte > Debugger) und stellen Sie sicher, dass das Kontrollkästchen **Step into external code** (In externen Code springen) aktiviert ist.

![Screenshot des Dialogfelds „Preferences“ (Voreinstellungen) mit dem Kontrollkästchen „Step into external code“ (In externen Code springen)](media/source-link1.png)

Sie können die Einstellung unter **Download External Code** (Externen Code herunterladen) nach Belieben ändern:
* Fragen: Visual Studio für Mac wird Sie auffordern, den externen Code herunterzuladen
* Immer: Visual Studio für Mac wird den externen Code automatisch herunterladen
* Nie: Visual Studio für Mac lädt den zugehörigen externen Code nicht herunter

Standardmäßig ist **Fragen** aktiviert. Sie erhalten die folgende Eingabeaufforderung, wenn ein externer Code für ein NuGet-Paket gefunden wird:

![Screenshot der Eingabeaufforderung, die angezeigt wird, wenn externer Code für ein NuGet-Paket gefunden wird](media/source-link2.png)


## <a name="see-also"></a>Siehe auch

- [SourceLink GitHub-Repository](https://github.com/dotnet/sourcelink/blob/master/README.md)
- Weitere Informationen zum Hinzufügen der SourceLink-Unterstützung zu Paketen finden Sie in der [.NET-Dokumentation](/dotnet/standard/library-guidance/sourcelink).