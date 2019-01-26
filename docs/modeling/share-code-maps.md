---
title: Exportieren und Speichern von Code maps
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: a4f53f349b4bc2f578ad007761df32e5c4145dbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984495"
---
# <a name="share-code-maps"></a>Freigeben von Code Maps

Sie können codeübersichten als Teil eines Visual Studio-Projekts, wie ein Bild oder als XPS-Datei speichern.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Freigeben Sie eine Code Map für andere Visual Studio-Benutzer.

Verwenden Sie das Menü **Datei** , um die Code Map zu speichern.

- oder - 

Wählen Sie zum Speichern der Zuordnung als Teil eines bestimmten Projekts auf der Symbolleiste der Map **Freigabe** > **verschieben \<CodeMapName > DGML in**, und wählen Sie dann auf das Projekt, in dem gespeichert werden soll, die die Zuordnung.

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

Wenn Sie eine Code Map als Bild exportieren, können Sie es in andere Anwendungen wie Microsoft Word oder PowerPoint kopieren.

1. Wählen Sie auf der Symbolleiste der Codeübersicht, **Freigabe** > **e-Mail als Bild versenden** oder **Bild kopieren**.

2. Fügen Sie das Bild in eine andere Anwendung ein.

## <a name="export-the-map-as-an-xps-file"></a>Exportieren der Code Map als XPS-Datei

Wenn Sie eine Code Map als XPS-Datei exportieren, können Sie es in XML- oder XAML-Viewern wie Internet Explorer finden Sie unter.

1. Wählen Sie auf der Symbolleiste der Codeübersicht, **Freigabe** > **E-Mail als portables XPS** oder **als portables XPS speichern**.

2. Durchsuchen Sie nach dem Ort, an dem die Datei gespeichert werden soll.

3. Benennen Sie die Code Map. Stellen Sie sicher, dass die **Dateityp** das Feld **XPS-Dateien (\*.xps)**. Wählen Sie **Speichern**.

## <a name="see-also"></a>Siehe auch

- [Zuordnen von Abhängigkeiten mit Code maps](../modeling/map-dependencies-across-your-solutions.md)