---
title: Projekte und Projektmappen
description: Dieses Dokument enthält eine Übersicht der Projekte und Projektmappen in Visual Studio für Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: ec62e9c0b449f5f2aed568735c2a10d1f6634eed
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820960"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekte und Projektmappen in Visual Studio für Mac

Dieser Artikel enthält eine Übersicht über die *Projekt* und *Lösung* Konzepte in Visual Studio für Mac.

> [!NOTE] 
> Dieses Thema gilt für Visual Studio für Mac. Visual Studio unter Windows, finden Sie unter [Projekte und Projektmappen in Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekte

Wenn eine neue Anwendung, Website usw. in Visual Studio für Mac zu erstellen, starten Sie mit einem Projekt ein. Das Projekt enthält alle erforderlichen Dateien (Quellcode, Bilder, Datendateien usw.), die erforderlich sind, um die ausführbare Datei, Bibliothek oder Website zu kompilieren.

Ein Projekt von einer Datei definiert ist (z. B. `.csproj` für C# Projekte) enthält Xml, das die Datei und die Ordnerhierarchie, die Pfade zu Dateien und projektspezifische Einstellungen, z. B. Buildeinstellungen definiert.

Wenn ein Projekt von Visual Studio für Mac geladen wird, verwendet Pad "Projektmappe" die Projektdatei, um die Dateien und Ordner in Ihrem Projekt anzuzeigen. Während der Kompilierung liest MSBuild die Einstellungen aus der Projektdatei, um die ausführbare Datei zu erstellen.

## <a name="solutions"></a>Projektmappen

Ein *Lösung* ist ein Container, die zusammen eine Gruppen oder mehreren verwandten Projekten. Lösungen werden von einer Textdatei beschrieben (Erweiterung `.sln`) mit einem individuellen Format; es sollte nicht manuell bearbeitet werden.

## <a name="managing-projects-in-the-solution-pad"></a>Verwalten von Projekten im Projektmappenpad

Nachdem ein Projekt erstellt oder geladen wurde, können Sie Pad "Projektmappe" zum Anzeigen und verwalten das Projekt oder Projektmappe und die darin enthaltenen Dateien. Die folgende Abbildung zeigt das Projektmappenpad mit einer .NET Core-Lösung, die zwei Projekte enthält:

![Beispielprojektmappe mit mehreren Projekten](media/solution-example.png)

Sie können die Eigenschaften von Projekten und Projektmappen verwalten, indem Sie entweder auf Doppelklicken auf den Namen des Projekts oder einer Projektmappe oder mit der rechten Maustaste, und wählen **Optionen**.

Weitere Informationen zu diesen Optionen finden Sie im Artikel [Verwalten von Projekt- und Projektmappeneigenschaften](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Siehe auch

- [Projektmappen und Projekte in Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
