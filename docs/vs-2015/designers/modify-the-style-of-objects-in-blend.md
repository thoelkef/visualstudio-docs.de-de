---
title: Ändern des Stils von Objekten in Blend | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ee1e1bc8762ae21ea69db5215d4dc472858d720
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442450"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Ändern des Stils von Objekten in Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die einfachste Möglichkeit zum Anpassen eines Objekts ist das Festlegen von Eigenschaften im Bereich **Eigenschaften**.  
  
 Wenn Sie Einstellungen oder Gruppen von Einstellungen erneut verwendet werden, erstellen Sie eine wieder verwendbare Ressource. Dies könnte ein *Stil*, eine *Vorlage* oder etwas so einfaches wie eine benutzerdefinierte Farbe sein. Sie können auch ein Steuerelement unterschiedlich basierend auf seine Status anzeigen. Beispielsweise wird eine Schaltfläche grün, wenn der Benutzer darauf klickt.  
  
 **In diesem Thema**:  
  
- [Pinsel: Ändern der Darstellung eines Objekts](#Brushes)  
  
- [Stile und Vorlagen: Erstellen eines konsistenten Aussehens und Verhaltens für Steuerelemente](#Styles)  
  
- [Visuelle Zustände: Ändern des Erscheinungsbilds eines Steuerelements basierend auf dessen Status](#Visual)  
  
- [Ressourcen: Farben, Stilen und Vorlagen zu erstellen und später erneut verwenden](#Resources)  
  
## <a name="Brushes"></a> Pinsel: Ändern des Aussehens eines Objekts  
 Anwenden eines Pinsels bei einem Objekt, dessen Darstellung geändert werden soll.  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Pinsel-Editor](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Zeichnen Sie ein sich wiederholendes Bild oder ein Muster für ein Objekt  
 Zeichnen Sie ein sich wiederholendes Bild oder ein Muster für ein Objekt mithilfe des *Kacheleffekts*.  
  
 Zum Erstellen eines Kacheleffekts erstellen Sie zunächst die Ressourcen *Bildpinsel*, *Zeichenpinsel* oder *visueller Pinsel*.  
  
 Erstellen Sie einen Bildpinsel mithilfe eines Bildes. Die folgenden Abbildungen zeigen den Bildpinsel, den Bildpinsel mit Kacheleffekt und den gekippten Bildpinsel.  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Erstellen Sie einen Zeichenpinsel mithilfe eines Vektors, indem Sie z. B. einen Pfad oder eine Form zeichnen. Die folgenden Abbildungen zeigen den Bildpinsel, den Bildpinsel mit Kacheleffekt und den gekippten Bildpinsel.  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Erstellen Sie einen visuellen Pinsel aus einem Steuerelement, z. B. einer Schaltfläche. Die folgenden Abbildungen zeigen den visuellen Pinsel und den visuellen Pinsel mit Kacheleffekt.  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Kachelpinsel](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
## <a name="Styles"></a> Stile und Vorlagen: Erstellen eines konsistenten Aussehens und Verhaltens für Steuerelemente  
 Sie entwerfen die Darstellung und das Verhalten eines Steuerelements einmal und wenden diesen Entwurf auf andere Steuerelemente an, sodass Sie sie nicht einzeln verwalten müssen.  
  
 **Sollten Sie einen Stil verwenden?**: Wenn Sie nur die Standardeigenschaften (z. B. die Farbe einer Schaltfläche) festlegen möchten, verwenden Sie einen *Stil*. Auch wenn Sie einen Stil angewendet haben, können Sie ein Steuerelement ändern.  
  
 **Sollten Sie eine Vorlage verwenden?**: Wenn Sie nur Text anzeigen möchten, können Sie eine *Vorlage* verwenden. Stellen Sie sich vor, Grafiken oder Logos in eine Schaltfläche zu konvertieren. Ein Steuerelement kann nicht geändert werden, nachdem Sie eine Vorlage angewendet haben.  
  
### <a name="create-a-template-or-style"></a>Erstellen einer Vorlage oder eines Stils  
 Es gibt zwei Möglichkeiten, eine Vorlage zu erstellen. Sie können ein Objekt auf der Zeichenfläche in ein Steuerelement konvertieren oder Sie können Ihre Vorlage auf ein vorhandenes Steuerelement stützen.  
  
 Um jedes Objekt in eine Steuerelementvorlage zu konvertieren, wählen Sie das Objekt, und klicken Sie dann auf das Menü **Extras** und wählen Sie **In Steuerelement konvertieren**.  
  
 Wenn Sie Ihre Vorlage basierend auf einem vorhandenen Steuerelement erstellen möchten, wählen Sie ein Objekt auf der Zeichenfläche. Klicken Sie dann oben auf der Zeichenfläche auf die Breadcrumb-Schaltfläche, wählen Sie dann **Vorlage bearbeiten** und danach **Kopie bearbeiten** oder **Leere erstellen**.  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Um einen Stil zu erstellen, wählen Sie das Objekt, und wählen Sie dann im Menü **Objekt** **Stil bearbeiten** und dann **Eine Kopie bearbeiten** oder **Leer erstellen**.  
  
- Wählen Sie **Kopie bearbeiten**, um mit dem Standardstil oder der Vorlage des Steuerelements zu beginnen.  
  
- Wählen Sie **Leere erstellen**, um von Grund auf neu zu starten.  
  
  Die Option **Aktuelle bearbeiten** erscheint nur, wenn Sie eine Formatvorlage oder Vorlage bearbeiten, die Sie bereits erstellt haben. Sie erscheint nicht für ein Steuerelement, das immer noch eine Standardvorlage für das System verwendet.  
  
  Im Dialogfeld **Stilressource erstellen** können Sie entweder den Stil oder die Vorlage so benennen, dass sie später verwendet werden kann, oder Sie können den Stil oder die Vorlage auf alle Steuerelemente des Typs anwenden.  
  
  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
> Sie können keine Stile oder Vorlagen für jede Art von Steuerelement erstellen. Wenn ein Steuerelement diese nicht unterstützt,  wird die Breadcrumb-Schaltfläche nicht oberhalb der Zeichenfläche angezeigt.  
>   
> Um zum Bearbeitungsbereich des Hauptdokuments zurückzukehren, klicken Sie auf **Return scope to** (Bereich zurücksetzen auf) ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
> ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Erstellen eines Stils](https://www.youtube.com/watch?v=W8YdXDPeKdc).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Anwenden von Stilen oder Vorlagen für ein Steuerelement  
 Rechtsklicken Sie auf ein Objekt im Bereich [Objekte und Zeitachse](http://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57), wählen Sie **Vorlage bearbeiten** und dann **Ressource anwenden**.  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Wiederherstellen des Standardstils oder der Vorlage eines Steuerelements  
 Wählen Sie das Steuerelement aus, und suchen Sie im Bereich [Eigenschaften](http://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) die Eigenschaft **Stil** oder **Vorlage**. Klicken Sie auf **Erweiterte Optionen** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb") und dann im Kontextmenü auf **Zurücksetzen**.  
  
## <a name="Visual"></a> Visuelle Zustände: Ändern der Darstellung eines Steuerelements basierend auf dessen Status  
 Steuerelemente können über unterschiedliche visuelle Darstellungen basierend auf Benutzerinteraktionen verfügen. Beispielsweise kann eine Schaltfläche grün werden, wenn ein Benutzer darauf klickt, oder Sie könnten eine Animation ausführen. Sie verkürzen oder verlängern die Zeit zwischen visuellen Zustände mithilfe von Übergängen.  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Verwalten des Zustands der WPF-Steuerelemente](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
## <a name="Resources"></a> Ressourcen: Erstellen von Farben, Stilen und Vorlagen und deren spätere Wiederverwendung  
 Sie können fast alles in Ihrem Projekt in eine Ressource konvertieren. Eine Ressource ist ein Objekt, das an unterschiedlichen Stellen in Ihrer Anwendung wiederverwendet werden kann. Sie können z. B. eine Farbe einmal erstellen, sie in eine Ressource konvertieren und dann diese Farbe auf mehrere Objekte anwenden. Um die Farbe aller dieser Objekte zu ändern, ändern Sie einfach die Farbressource.  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-b153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [eine kurze Fingereingabe auf Ressourcen](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
