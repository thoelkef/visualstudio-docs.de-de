---
title: "&#196;ndern des Stils von Objekten in Blend | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# &#196;ndern des Stils von Objekten in Blend
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die einfachste Möglichkeit zum Anpassen eines Objekts ist das Festlegen von Eigenschaften im Bereich **Eigenschaften**.  
  
 Wenn Sie Einstellungen oder Gruppen von Einstellungen erneut verwendet werden, erstellen Sie eine wieder verwendbare Ressource.  Dies könnte möglicherweise eine *Stil\-*, *Vorlage* oder etwas so einfaches wie eine benutzerdefinierte Farbe sein.  Sie können auch ein Steuerelement unterschiedlich basierend auf seine Status anzeigen.  Beispielsweise wird eine Schaltfläche grün, wenn der Benutzer darauf klickt.  
  
 **In diesem Abschnitt**:  
  
-   [Pinsel: Ändern des Erscheinungsbilds einen Objekts](#Brushes)  
  
-   [Stile und Vorlagen: Erstellen eines konsistenten Aussehens und Verhaltens für Steuerelemente](#Styles)  
  
-   [Visuelle Zustände: Ändern des Erscheinungsbilds eines Steuerelements basierend auf dessen Status](#Visual)  
  
-   [Ressourcen: Künftige erneute Verwendung von Farben, Stilen und Vorlagen](#Resources)  
  
##  <a name="Brushes"></a> Pinsel: Ändern des Erscheinungsbilds einen Objekts  
 Anwenden eines Pinsels bei einem Objekt, dessen Darstellung geändert werden soll.  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Pinsel\-Editor](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### Zeichnen Sie ein sich wiederholendes Bild oder ein Muster für ein Objekt  
 Zeichnen Sie ein sich wiederholendes Bild oder ein Muster für ein Objekt mithilfe eines *Kacheleffekts*.  
  
 Zum Erstellen eines Kacheleffekts erstellen Sie zunächst eine Ressource *Bildpinsel*, *Zeichenpinsel* oder *visueller Pinsel*.  
  
 Erstellen Sie einen Bildpinsel mithilfe eines Bildes.  Die folgenden Abbildungen zeigen den Bildpinsel, den Bildpinsel mit Kacheleffekt und den gekippten Bildpinsel.  
  
 Erstellen Sie einen Zeichenpinsel mithilfe eines Vektors, indem Sie z. B. einen Pfad oder eine Form zeichnen.  Die folgenden Abbildungen zeigen den Bildpinsel, den Bildpinsel mit Kacheleffekt und den gekippten Bildpinsel.  
  
 Erstellen Sie einen visuellen Pinsel aus einem Steuerelement, z. B. einer Schaltfläche.  Die folgenden Abbildungen zeigen den visuellen Pinsel und den visuellen Pinsel mit Kacheleffekt.  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Kachelpinsel](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Stile und Vorlagen: Erstellen eines konsistenten Aussehens und Verhaltens für Steuerelemente  
 Sie entwerfen die Darstellung und das Verhalten eines Steuerelements einmal und wenden diesen Entwurf auf andere Steuerelemente an, sodass Sie sie nicht einzeln verwalten müssen.  
  
 **Sollten Sie einen Stil verwenden?** Wenn Sie nur die Standardeigenschaften \(beispielsweise die Farbe einer Schaltfläche\) festlegen möchten, verwenden Sie einen *Stil*.  Auch wenn Sie einen Stil angewendet haben, können Sie ein Steuerelement ändern.  
  
 **Sollten Sie eine Vorlage verwenden?** Wenn Sie die Struktur des Steuerelements ändern möchten, verwenden Sie eine *Vorlage*.  Stellen Sie sich vor, Grafiken oder Logos in eine Schaltfläche zu konvertieren.  Ein Steuerelement kann nicht geändert werden, nachdem Sie eine Vorlage angewendet haben.  
  
### Erstellen einer Vorlage oder eines Stils  
 Es gibt zwei Möglichkeiten, eine Vorlage zu erstellen.  Sie können ein Objekt auf der Zeichenfläche in ein Steuerelement konvertieren oder Sie können Ihre Vorlage auf ein vorhandenes Steuerelement stützen.  
  
 Um jedes Objekt in eine Steuerelementvorlage zu konvertieren, wählen Sie das Objekt, und klicken Sie dann auf das Menü **Extras** und wählen Sie **In Steuerelement konvertieren**.  
  
 Wenn Sie Ihre Vorlage basierend auf einem vorhandenen Steuerelement erstellen möchten, wählen Sie ein Objekt auf der Zeichenfläche.  Klicken Sie dann oben auf der Zeichenfläche auf die Breadcrumb\-Schaltfläche, wählen Sie dann **Vorlage bearbeiten** und danach **Kopie bearbeiten** oder **Leere erstellen**.  
  
 Um einen Stil zu erstellen, wählen Sie das Objekt, und wählen Sie dann im Menü **Objekt Stil bearbeiten** und dann **Eine Kopie bearbeiten** oder **Leer erstellen**.  
  
-   Wählen Sie **Kopie bearbeiten**, um mit dem Standardstil oder der Vorlage des Steuerelements zu beginnen.  
  
-   Wählen Sie **Leere erstellen**, um von Grund auf neu zu starten.  
  
 Die Option **Aktuelle bearbeiten** erscheint nur, wenn Sie einen Stil oder eine Vorlage bearbeiten, die Sie bereits erstellt haben.  Sie erscheint nicht für ein Steuerelement, das immer noch eine Standardvorlage für das System verwendet.  
  
 Im Dialogfeld **Stilressource erstellen** können Sie entweder den Stil oder die Vorlage so benennen, dass sie später verwendet werden kann, oder Sie können den Stil oder die Vorlage auf alle Steuerelemente des Typs anwenden.  
  
> [!NOTE]
>  Sie können keine Stile oder Vorlagen für jede Art von Steuerelement erstellen.  Wenn ein Steuerelement diese nicht unterstützt,  wird die Breadcrumb\-Schaltfläche nicht oberhalb der Zeichenfläche angezeigt.  
>   
>  Um zum Bearbeitungsbereich des Hauptdokuments zurückzukehren, klicken Sie auf **Bereich zurücksetzen auf** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3\-ed98\-4f20\-aa66\-a6f5b23eeb2b").  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Erstellen eines Stils](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Erstellen einer Steuerelementvorlage in Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### Anwenden von Stilen oder Vorlagen für ein Steuerelement  
 Rechtsklicken Sie auf ein Objekt im Bereich [Objekte und Zeitachse](http://msdn.microsoft.com/de-de/135a5a5e-ec6d-4f38-8827-60e284cd5f57), wählen Sie **Vorlage bearbeiten** und dann **Ressource anwenden**.  
  
### Wiederherstellen des Standardstils oder der Vorlage eines Steuerelements  
 Wählen Sie das Steuerelement aus, und suchen Sie im Bereich [Eigenschaften](http://msdn.microsoft.com/de-de/135a5a5e-ec6d-4f38-8827-60e284cd5f57) die Eigenschaft **Stil** oder **Vorlage**.  Klicken Sie auf **Erweiterte Optionen** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962\-5d8a\-480d\-a837\-e06b84c545bb") und dann auf **Zurücksetzen** im Kontextmenü.  
  
##  <a name="Visual"></a> Visuelle Zustände: Ändern des Erscheinungsbilds eines Steuerelements basierend auf dessen Status  
 Steuerelemente können über unterschiedliche visuelle Darstellungen basierend auf Benutzerinteraktionen verfügen.  Beispielsweise kann eine Schaltfläche grün werden, wenn ein Benutzer darauf klickt, oder Sie könnten eine Animation ausführen.  Sie verkürzen oder verlängern die Zeit zwischen visuellen Zustände mithilfe von Übergängen.  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Verwalten Sie den Status der WPF\-Steuerelemente](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Ressourcen: Künftige erneute Verwendung von Farben, Stilen und Vorlagen  
 Sie können fast alles in Ihrem Projekt in eine Ressource konvertieren.  Eine Ressource ist ein Objekt, das an unterschiedlichen Stellen in Ihrer Anwendung wiederverwendet werden kann.  Sie können z. B. eine Farbe einmal erstellen, sie in eine Ressource konvertieren und dann diese Farbe auf mehrere Objekte anwenden.  Um die Farbe aller dieser Objekte zu ändern, ändern Sie einfach die Farbressource.  
  
 **Sehen Sie sich ein kurzes Video an \(womöglich nur in englischer Sprache\):** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Eine kurze Fingereingabe auf Ressourcen](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## Siehe auch  
 [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)