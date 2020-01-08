---
title: 'Vorgehensweise: Exportieren einer Textur, die Mipmaps enthält'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589408"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Vorgehensweise: Exportieren einer Textur, die Mipmaps enthält

Mit der Bildinhaltspipeline können Mipmaps aus einem Quellbild als Teil der Buildphase des Projekts generiert werden. Sie müssen manchmal den Bildinhalt für jede MIP-Ebene manuell angeben, um bestimmte Effekte zu erzielen. Wenn Sie den Bildinhalt jeder MIP-Ebene nicht manuell angeben müssen, stellt das Generieren von Mipmaps zur Buildzeit sicher, dass die Inhalte von Mipmaps stets synchronisiert werden. Dadurch werden ebenfalls die Leistungseinbußen durch das Generieren von Mipmaps zur Laufzeit vermieden.

Dieser Artikel behandelt Folgendes:

- Konfigurieren des Quellbilds für die Verarbeitung mithilfe der Pipeline für Bildinhalte.

- Konfigurieren der Pipeline für Bildinhalte zum Generieren von Mipmaps.

## <a name="export-mipmaps"></a>Exportieren von Mipmaps

Mipmapping stellt im Bildschirmbereich automatisch die Detailebene für strukturierte Oberflächen in einem 3D-Spiel oder einer 3D-App bereit. Dadurch wird die Leistung beim Rendern eines Spiels oder einer App verbessert, indem komprimierte Versionen einer Textur im Voraus berechnet werden. Das Berechnen von komprimierten Versionen im Voraus bedeutet, dass beim Sampling nicht jedes Mal die gesamte Textur komprimiert werden muss.

### <a name="to-export-a-texture-that-has-mipmaps"></a>So exportieren Sie eine Textur mit Mipmaps

1. Beginnen Sie mit einer Standardtextur. Laden Sie eine vorhandene Datei, oder erstellen Sie eine, wie in [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md) beschrieben. Um Mipmaps zu unterstützen geben Sie eine Textur mit einer Breite und Höhe an, die beide in der Größe über die gleiche Potenz verfügen, z. B. 64x64, 256x256 oder 512x512.

2. Konfigurieren Sie die soeben erstellte Texturdatei so, dass sie durch die Pipeline für Bildinhalte verarbeitet wird. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die erstellte Texturdatei, und klicken Sie dann auf **Eigenschaften**. Legen Sie anschließend die Eigenschaft **Elementtyp** auf der Seite **Konfigurationseigenschaften** > **Allgemein** auf **Pipeline für Bildinhalte** fest. Überprüfen Sie, ob die Eigenschaft **Inhalt** auf **Ja** und **Vom Build ausschließen** auf **Nein** festgelegt ist. Klicken Sie auf **Übernehmen**.

   Die Eigenschaftenseite für die Konfiguration der **Pipeline für Bildinhalte** wird angezeigt.

3. Konfigurieren Sie die Pipeline für Bildinhalte so, dass sie Mipmaps generiert. Legen Sie die Eigenschaft **MIPS generieren** auf der Seite **Konfigurationseigenschaften** > **Pipeline für Bildinhalte** > **Allgemein** auf **Ja (/generatemips)** fest.

4. Klicken Sie auf **OK**.

Wenn Sie das Projekt erstellen, wird das Quellbild (einschließlich MIP-Ebenen) von der Pipeline für Bildinhalte vom Arbeitsformat in das angegebene Ausgabeformat konvertiert. Das Ergebnis wird dann in das Ausgabeverzeichnis des Projekts kopiert.
