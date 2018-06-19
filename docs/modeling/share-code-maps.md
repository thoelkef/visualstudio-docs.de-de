---
title: Exportieren und Speichern von Code maps
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268375"
---
# <a name="share-code-maps"></a>Freigeben von Code Maps

Sie können Code Maps als Teil eines Visual Studio-Projekts, als Bild oder als XPS-Datei speichern.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Freigeben Sie eine Code Map für andere Visual Studio-Benutzer

Verwenden Sie das Menü **Datei** , um die Code Map zu speichern.

- oder - 

Um die Karte als Teil eines bestimmten Projekts auf der Symbolleiste der Map zu speichern, wählen Sie **Freigabe** > **verschieben \<CodeMapName > DGML in**, und wählen Sie dann das Projekt, in dem gespeichert werden soll, die die Zuordnung.

![Verschieben einer Zuordnung in ein anderes Projekt](../modeling/media/codemapsmovemapmenu.png)

Visual Studio speichert die Zuordnung als eine *DGML* -Datei, die Sie für andere Benutzer von Visual Studio Enterprise und Visual Studio Professional freigeben können.

> [!NOTE]
> Vergewissern Sie sich, dass alle Gruppen erweitert sind, alle ausgeblendeten Knoten und gruppenübergreifenden Links angezeigt werden, und rufen Sie alle gelöschten Knoten ab, die andere in der Code Map sehen sollen, bevor Sie eine Code Map für Benutzer von Visual Studio Professional freigeben. Andernfalls können andere Benutzer diese Elemente nicht sehen.
>
> Wenn Sie eine Code Map speichern, die sich in einem Modellierungsprojekt befindet oder von einem Modellierungsprojekt an einen anderen Speicherort kopiert wurde, tritt möglicherweise der folgende Fehler auf:
>
> " *Dateiname* kann nicht außerhalb des Projektverzeichnisses gespeichert werden. Verknüpfte Elemente werden nicht unterstützt."
>
> Der Fehler wird zwar von Visual Studio angezeigt, die Version wird aber dennoch gespeichert. Erstellen Sie die Code Map außerhalb des Modellierungsprojekts, um diesen Fehler zu vermeiden. Sie können es anschließend am gewünschten Speicherort speichern. Es wird nicht funktionieren, die Datei einfach an eine andere Position in der Projektmappe zu kopieren und dort zu speichern.

## <a name="export-a-code-map-as-an-image"></a>Exportieren Sie eine Code Map als Bild

Wenn Sie eine Code Map als Bild exportieren, können Sie ihn in andere Anwendungen, z. B. Microsoft Word oder PowerPoint kopieren.

1. Wählen Sie auf der Symbolleiste der Code Map **Freigabe** > **als Bild per e-Mail senden** oder **Bild kopieren**.

2. Fügen Sie das Bild in eine andere Anwendung ein.

## <a name="export-the-map-as-an-xps-file"></a>Exportieren der Code Map als XPS-Datei

Wenn Sie eine Code Map als XPS-Datei exportieren, können Sie es im XML- oder XAML-Viewern wie Internet Explorer sehen.

1. Wählen Sie auf der Symbolleiste der Code Map **Freigabe** > **E-Mail als portables XPS** oder **als portables XPS speichern**.

2. Durchsuchen Sie nach dem Ort, an dem die Datei gespeichert werden soll.

3. Benennen Sie die Code Map. Stellen Sie sicher, dass die **Dateityp** das Feld **XPS-Dateien (\*.xps)**. Wählen Sie **Speichern**.

## <a name="see-also"></a>Siehe auch

- [Zuordnen von Abhängigkeiten mit Code maps](../modeling/map-dependencies-across-your-solutions.md)