---
title: 'Vorgehensweise: Erstellen einer Basistextur | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a19cd0b68927effc32b0480fdeb7286be8ad8dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664574"
---
# <a name="how-to-create-a-basic-texture"></a>Gewusst wie: Erstellen einer Basistextur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie die Bildbearbeitung zum Erstellen einer Basistextur verwendet wird.

 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:

- Festlegen der Texturgröße

- Festlegen der Vorder -und Hintergrundfarben

- Verwenden des Alphakanals (Transparenz)

- Verwenden der Tools **Füllung** und **Ellipse**

- Festlegen der Tooleigenschaften

## <a name="creating-a-basic-texture"></a>So erstellen Sie eine Basistextur
 Sie können die Bildbearbeitung zum Erstellen und Ändern von Bildern und Texturen Ihre Spiele und Anwendungen verwenden.

 In den folgenden Schritten wird gezeigt, wie eine Textur erstellt wird, die einer Zielscheibe darstellt. Wenn Sie fertig sind, sollte die Textur wie im folgenden Bild aussehen. Die Bildbearbeitung wurde so eingestellt, dass ein grünes, kariertes Muster zur Darstellung verwendet wird, um die Transparenz in der Textur besser zu veranschaulichen.

 ![Zielscheibe mit Transparenz in Grün](../designers/media/digit-bullseye-texture-in-editor.png "Digit-Bull Sekunden-Textur-in-Editor")

 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** angezeigt wird. Verwenden Sie während dem Arbeiten das Fenster **Eigenschaften**, um die Bildgröße festzulegen, Tooleigenschaften zu ändern und Farben anzugeben.

#### <a name="to-create-a-bullseye-target-texture"></a>So erstellen Sie eine Textur der Zielscheibe

1. Erstellen Sie eine Textur, mit der Sie arbeiten können. Weitere Informationen zum Hinzufügen von Texturen zu Projekten finden Sie im Abschnitt „Erste Schritte“ unter [Bildbearbeitung](../designers/image-editor.md).

2. Legen Sie die Bildgröße auf 512 x 512 Pixel fest. Geben Sie im Fenster **Eigenschaften** die Werte der Eigenschaften **Breite** und **Höhe** für `512` an.

3. Klicken Sie auf der Symbolleiste der Bildbearbeitung auf das Tool **Füllung**. Das Fenster **Eigenschaften** zeigt nun die Eigenschaften des Tools **Füllung** zusammen mit den Bildeigenschaften an.

4. Legen Sie die Vordergrundfarbe auf vollständig transparentes schwarz fest. Klicken Sie in der Eigenschaftengruppe **Farben** im Fenster **Eigenschaften** auf **Vordergrund**. Legen Sie die Werte der Eigenschaften **R**, **G**, **B** und **A** neben dem Farbwähler auf `0` fest.

5. Klicken Sie auf der Symbolleiste der Bildbearbeitung auf das Tool **Füllung**. Halten Sie anschließend die Umschalttaste gedrückt, und wählen Sie einen beliebigen Punkt im Bild aus. Indem die Umschalttaste verwendet wird, ersetzt der Alphawert der Füllfarbe die Farbe im Bild; ansonsten wird der Alphawert verwendet, um die Füllfarbe mit der Farbe im Bild zu vermischen.

   > [!IMPORTANT]
   > Dieser Schritt stellt zusammen mit der Farbauswahl im vorherigen Schritt sicher, dass das Basisbild für die Zielscheibentextur vorbereitet ist, die Sie zeichnen werden. Wenn das Bild mit transparentem Schwarz gefüllt ist, und, da der Rahmen des Ziels schwarz ist, wird es keine Aliasing-Artefakte um das Ziel herum geben.

6. Klicken Sie auf der Symbolleiste der Bildbearbeitung auf das Tool **Ellipse**.

7. Legen Sie die Vordergrundfarbe auf ein vollständig deckendes schwarz fest. Legen Sie die Werte der Eigenschaften **R**, **G** und **B**`0` sowie den Wert der Eigenschaft **A** auf `255` fest.

8. Legen Sie die Hintergrundfarbe auf ein vollständig deckendes weiß fest. Klicken Sie in der Eigenschaftengruppe **Farben** im Fenster **Eigenschaften** auf **Hintergrund**. Legen Sie die Werte der Eigenschaften **R**, **G**, **B** und **A** auf `255` fest.

9. Legen Sie die Breite der Kontur der Ellipse fest. Legen Sie in der Eigenschaftengruppe **Aussehen** im Fenster **Eigenschaften** den Wert der Eigenschaft **Breite** auf `8` fest.

10. Stellen Sie sicher, dass Anti-Aliasing aktiviert ist. Stellen Sie sicher, dass in der Eigenschaftengruppe **Aussehen** im Fester **Eigenschaften** die Eigenschaft **Anti-Alias** festgelegt ist.

11. Zeichnen Sie mithilfe des Tools **Ellipse** einen Kreis von Pixelkoordinate `(3, 3)` bis Pixelkoordinate `(508, 508)`. Sie können während dem Zeichnen die Umschalttaste drücken und gedrückt halten, um den Kreis einfacher zu zeichnen.

    > [!NOTE]
    > Die Pixelkoordinaten der aktuellen Zeigerposition werden auf der Statusleiste [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt.

12. Ändern Sie die Hintergrundfarbe. Legen Sie **R** auf `44`, **G** auf `165`, **B** auf `211` und **A** auf `255` fest.

13. Zeichnen Sie einen weiteren Kreis von Pixelkoordinate `(64, 64)` bis Pixelkoordinate `(448, 448)`.

14. Ändern Sie die Hintergrundfarbe auf ein vollständig deckendes weiß. Legen Sie **R**, **G**, **B** und **A** auf `255` fest.

15. Zeichnen Sie einen weiteren Kreis von Pixelkoordinate `(128, 128)` bis Pixelkoordinate `(384, 384)`.

16. Ändern Sie die Hintergrundfarbe. Legen Sie **R** auf `255`, **G** und **B** auf `64` sowie **A** auf `255` fest.

17. Zeichnen Sie einen weiteren Kreis von Pixelkoordinate `(192, 192)` bis Pixelkoordinate `(320, 320)`.

    Die vollständige Textur der Zielscheibe Hier ist das endgültige Bild, das mit Transparenz gezeigt wird.

    ![Die vollständige Textur der Zielscheibe](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")

    Als nächsten Schritt können Sie die MIP-Ebenen dieser Textur generieren. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Ändern von MIP-Ebenen](../designers/how-to-create-and-modify-mip-levels.md)

## <a name="see-also"></a>Weitere Informationen
 [Bildbearbeitung](../designers/image-editor.md)
