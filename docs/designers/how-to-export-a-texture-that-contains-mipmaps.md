---
title: "Vorgehensweise: Erstellen einer Textur, die Mipmaps enthält | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 2176086d813109a92f1e2467498d3f1ad4b18c5e
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Gewusst wie: Erstellen einer Textur, die Mipmaps enthält
Mit der Bildinhaltspipeline können Mipmaps aus einem Quellbild als Teil der Buildphase des Projekts generiert werden. Wenn Sie den Bildinhalt jeder MIP-Ebene nicht manuell angeben müssen (wie es bei bestimmten Effekten der Fall ist) stellt das Generieren von Mipmaps zur Buildzeit sicher, dass Mipmapinhalte niemals unsynchronisiert sind und dass die Leistungseinbußen bei der Generierung von Mipmaps zur Laufzeit ausgeschlossen werden.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Konfigurieren des Quellbilds für die Verarbeitung mithilfe der Pipeline für Bildinhalte.  
  
-   Konfigurieren der Pipeline für Bildinhalte zum Generieren von Mipmaps.  
  
## <a name="exporting-mipmaps"></a>Exportieren von Mipmaps  
 Mipmapping stellt im Bildschirmbereich automatisch die Detailebene für strukturierte Oberflächen in einem 3D-Spiel oder einer 3D-App bereit. Die Renderingleistung eines Spiels oder einer App wird mithilfe von vorberechneter komprimierter Versionen einer Textur erhöht, damit nicht jedes Mal die gesamte Textur komprimiert werden muss.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>So exportieren Sie eine Textur mit Mipmaps  
  
1.  Beginnen Sie mit einer Standardtextur. Laden Sie eine vorhandene Datei, oder erstellen Sie eine, wie in [Vorgehensweise: Erstellen einer Basistextur](../designers/how-to-create-a-basic-texture.md) beschrieben. Um Mipmaps zu unterstützen geben Sie eine Textur mit einer Breite und Höhe an, die beide in der Größe über die gleiche Potenz verfügen, z. B. 64x64, 256x256 oder 512x512.  
  
2.  Konfigurieren Sie die soeben erstellte Texturdatei so, dass sie durch die Pipeline für Bildinhalte verarbeitet wird. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die soeben erstellte Texturdatei, und wählen Sie dann **Eigenschaften** aus. Legen Sie anschließend die Eigenschaft **Elementtyp** auf der Seite **Konfigurationseigenschaften**, **Allgemein** auf **Pipeline für Bildinhalte** fest. Stellen Sie sicher, dass die Eigenschaft **Inhalt** auf **Ja** und die Option **Aus Build ausschließen** auf **Nein** festgelegt ist. Wählen Sie dann die Schaltfläche **Übernehmen** aus. Die Eigenschaftenseite für die Konfiguration der **Pipeline für Bildinhalte** wird angezeigt.  
  
3.  Konfigurieren Sie die Pipeline für Bildinhalte so, dass sie Mipmaps generiert. Legen Sie die Eigenschaft **MIPS generieren** auf der Seite **Konfigurationseigenschaften**, **Pipeline für Bildinhalte**, **Allgemein** auf **JA (/generatemips)** fest.  
  
4.  Klicken Sie auf die Schaltfläche **OK** .  
  
 Wenn Sie das Projekt erstellen, wird das Quellbild von der Pipeline für Bildinhalte vom Arbeitsformat in das angegebene Ausgabeformat konvertiert, einschließlich MIP-Ebenen. Das Ergebnis wird dann in das Ausgabeverzeichnis des Projekts kopiert.
