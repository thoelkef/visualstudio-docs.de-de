---
title: Erstellen und Bereinigen von Projekten und Projektmappen
description: In diesem Artikel erfahren Sie, wie Sie in Visual Studio für Mac ein Projekt erstellen.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128453"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Erstellen und Bereinigen von Projekten und Projektmappen

Führen Sie die in diesem Artikel aufgeführten Schritte aus, um zu erfahren, wie Sie alle oder einige der Projekte in einer Projektmappe erstellen, neu erstellen oder bereinigen.

> [!NOTE]
> Dieses Thema gilt für Visual Studio für Mac. Informationen für Visual Studio unter Windows finden Sie unter [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>So können Sie eine gesamte Projektmappe erstellen, neu erstellen oder bereinigen

1. Klicken Sie im **Lösungspad** auf den Knoten „Projektmappe“:

    ![Auswählen des Knotens „Projektmappe“](media/compiling-and-building-image1.png)

2. Klicken Sie in der Menüleiste auf das Menü **Erstellen**, und wählen Sie dann eine der folgenden Optionen aus:

    ![Auswählen des Menüelements „Build All“](media/compiling-and-building-image2.png)

    * Wählen Sie **Alle erstellen** aus, um die Dateien und Komponenten innerhalb des Projekts zu kompilieren, die seit dem letzten Build geändert wurden.

    * Wählen Sie **Alle neu erstellen** aus, um die Projektmappe zu „bereinigen“ und anschließend alle Projektdateien und Komponenten neu zu erstellen.

    * Wählen Sie **Alle bereinigen** aus, um alle Zwischen- und Ausgabedateien zu löschen. Dann bleiben nur die Projekt- und Komponentendateien übrig, und neue Instanzen der Interims- und Ausgabedateien können erstellt werden.

## <a name="to-build-or-rebuild-a-single-project"></a>So erstellen Sie ein einzelnes Projekt oder erstellen es neu

1. Wählen Sie das Projekt im **Lösungspad** aus.

2. Wählen Sie in der Menüleiste das Menü **Build** aus.

3. Wählen Sie entweder „[Projektname] erstellen“, „[Projektname] neu erstellen“ oder „[Projektname] bereinigen“ aus.

## <a name="to-stop-a-build"></a>So beenden Sie einen Build

Verwenden Sie eine der folgenden Optionen, um ein Build zu beenden:

* Klicken Sie im Statusbereich auf das rote Quadrat:

    ![Klicken auf das rote Quadrat, um den Build zu beenden](media/compiling-and-building-image3.png)

* Verwenden Sie das Element **Stoppen** im Menü **Build**.

* Drücken Sie **CMD + UMSCHALT + EINGABETASTE**.

## <a name="see-also"></a>Siehe auch

- [Erstellen und Bereinigen von Projekten und Projektmappen (Visual Studio unter Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)