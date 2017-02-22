---
title: "Gewusst wie: Erstellen einer Basistextur | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 15
caps.handback.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Gewusst wie: Erstellen einer Basistextur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dokument wird die Verwendung des Bild\-Editors zur Erstellung einer Basistextur veranschaulicht.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Festlegen der Größe der Textur  
  
-   Festlegen des Vordergrunds und der Hintergrundfarbe  
  
-   Verwenden des Alphakanals \(Transparenz\)  
  
-   Verwenden der **Ausfüllen** und der **Ellipse** Tools  
  
-   Festlegen von Tooleigenschaften  
  
## Erstellen einer Standadtextur  
 Sie können den Grafik\-Editor verwenden, um Bilder und Texturen für Ihr Spiel oder Ihre App erstellen und zu ändern.  
  
 Die folgenden Schritte zeigen, wie eine Textur erstellt, der ein "Bullaugen" Ziel darstellt. Wenn Sie fertig sind, sollte die Textur wie im folgenden Bild aussehen.  Um die Transparenz in der Textur besser zu veranschaulichen, ist der Grafik\-Editor konfiguriert wurde um ein Grün, kariertes Muster verwenden um es anzuzeigen.  
  
 ![Zielscheibe mit Transparenz in Grün](../designers/media/digit-bullseye-texture-in-editor.png "Digit\-Bullseye\-Texture\-In\-Editor")  
  
 Bevor Sie beginnen, sicher, dass das Fenster **Eigenschaften** angezeigt wird.  Verwenden Sie das Fenster **Eigenschaften**, um die Größe festzulegen, ändern Tooleigenschaften und geben Farben, während Sie arbeiten.  
  
#### So eine "Bullaugen" Zieltextur erstellen  
  
1.  Erstellen Sie eine Textur, mit der Sie arbeiten können.  Weitere Informationen zum Hinzufügen von Texturen zu Projekten finden Sie im Abschnitt "Erste Schritte" in [Grafik\-Editor](../designers/image-editor.md).  
  
2.  Legen Sie die Größe auf 512x512 Pixel fest.  Im Fenster **Eigenschaften** legen Sie die Werte **Breite** und Eigenschaften auf `512`**Höhe** fest.  
  
3.  Auf der Symbolleiste des Grafik\-Editors wählen Sie das Tool **Ausfüllen** aus.  Das Fenster **Eigenschaften** werden die Eigenschaften des **Ausfüllen** Tools sowie die Bildeigenschaften an.  
  
4.  Legen Sie die voll\-transparentes Vordergrundfarbe auf Schwarz fest.  Im Fenster **Eigenschaften** in der Eigenschaftengruppe **Farben**, wählen Sie **Vordergrund** aus.  Legen Sie die Werte **R**, **G**, **B** und Eigenschaften **A** neben der Farbauswahl für `0` fest.  
  
5.  Auf der Symbolleiste des Grafik\-Editors wählen Sie das Tool **Ausfüllen** aus, und halten Sie die UMSCHALTTASTE gedrückt und wählen Sie einen Punkt im Bild.  Verwenden der UMSCHALTTASTE wird der Alphawert der Füllfarbe, die Farbe im Bild zu ersetzen; Andernfalls wird der Alphawert verwendet, um die Füllfarbe zusammen mit der Farbe im Bild zu verschmelzen.  
  
    > [!IMPORTANT]
    >  Dieser Schritt, zusammen mit der Farbauswahl im vorherigen Schritt, wird sichergestellt, dass das Ausgangsbild für die "Bullaugen" Zieltextur vorbereitet wird, die Sie zeichnen.  Wenn das Bild mit transparentem gefüllt wird Schwarz\- und da der Kontext des Ziels ist, keine Schwarz\-dort Aliasingartefakte um das Ziel ist.  
  
6.  Auf der Symbolleiste des Grafik\-Editors wählen Sie das Tool **Ellipse** aus.  
  
7.  Legen Sie die Vordergrundfarbe auf vollständig deckendes Schwarz fest.  Legen Sie die Werte der Eigenschaften **R**, **G** und **B** auf `0` und des Werts der Eigenschaft **A** auf `255` fest.  
  
8.  Festlegen der Hintergrundfarbe auf vollständig deckendes Weiß fest.  Im Fenster **Eigenschaften** in der Eigenschaftengruppe **Farben**, wählen Sie **Hintergrund** aus.  Legen Sie die Werte **R**, **G**, **B** und Eigenschaften auf `255`**A** fest.  
  
9. Legen Sie die Breite der Kontur der Ellipse fest.  Im Fenster **Eigenschaften** in der Eigenschaftengruppe **Darstellung** Satz, der Wert der Eigenschaft **Breite** zu `8`.  
  
10. Überprüfen Sie, ob Antialiasing aktiviert ist.  Im Fenster **Eigenschaften** in der Eigenschaftengruppe **Darstellung**, überprüfen Sie, ob die Eigenschaft **Antialiasing:** festgelegt wird.  
  
11. Verwenden des Tools **Ellipse** zeichnen Sie einen Kreis von Pixelkoordinate `(3, 3)` zu Pixelkoordinate. `(508, 508)` Um den Kreis leicht zu zeichnen, können Sie die UMSCHALTTASTE gedrückt halten während Sie zeichnen.  
  
    > [!NOTE]
    >  Die Pixelkoordinaten des aktuellen Zeigerspeicherorts [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden auf der Statusleiste angezeigt.  
  
12. Ändern der Hintergrundfarbe.  **R** festgelegt wird `44`, auf `165`**G**, **B** `211` und **A** zu `255`.  
  
13. Zeichnen Sie einen Kreis von anderen Pixelkoordinate `(64, 64)` zu Pixelkoordinate. `(448, 448)`  
  
14. Ändern der Hintergrundfarbe wieder auf Weiß vollständig deckend.  **R** festgelegt, **G**, **B** und **A** zu `255`.  
  
15. Zeichnen Sie einen Kreis von anderen Pixelkoordinate `(128, 128)` zu Pixelkoordinate. `(384, 384)`  
  
16. Ändern der Hintergrundfarbe.  **R** festgelegt zu `255`, **G** und **B** `64` und **A** zu `255`.  
  
17. Zeichnen Sie einen Kreis von anderen Pixelkoordinate `(192, 192)` zu Pixelkoordinate. `(320, 320)`  
  
 Die "Bullaugen" Zieltextur ist vollständig.  Es folgt das endgültige Bild angezeigt, mit Transparenz.  
  
 ![Die vollständige Textur der Zielscheibe](../designers/media/gfx_image_demo_bullseye.png "gfx\_image\_demo\_bullseye")  
  
 Als nächster Schritt können Sie MIP\-Ebenen für diese Textur generieren.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen und Ändern von MIP\-Ebenen](../designers/how-to-create-and-modify-mip-levels.md).  
  
## Siehe auch  
 [Grafik\-Editor](../designers/image-editor.md)