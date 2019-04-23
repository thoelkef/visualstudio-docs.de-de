---
title: Organisieren von Objekten in Layout-Containern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ca6fc205585d832f4dadc5f4ce4709a71c7b6fe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059200"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organisieren von Objekten in Layoutcontainern im XAML-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellen Sie sich vor, wo Objekte auf einer Seite angezeigt werden sollen; Objekte wie Bilder, Schaltflächen und Videos. Möglicherweise sollen sie in Zeilen und Spalten in einer einzigen Zeile, vertikal oder horizontal oder an festen Positionen anzeigt werden.  
  
 Nachdem Sie die Möglichkeit gehabt haben, darüber nachzudenken, wie die Seite angezeigt werden kann, wählen Sie ein LayoutPanel-Element. Alle Seiten starten mit einem, da Ihre Objekte zu etwas hinzugefügt werden müssen. Standardmäßig handelt es sich zwar um ein **Raster**, aber Sie können dies ändern.  
  
 LayoutPanel-Elemente helfen Ihnen, Objekte auf einer Seite anzuordnen, aber sie können noch mehr. Sie helfen Ihnen, für verschiedene Bildschirmgrößen und Auflösungen zu entwerfen. Wenn Benutzer Ihre Anwendung ausführen, wird alles in einem Layoutpanel passend zur Bildschirmfläche des Geräts angepasst. Wenn Sie dies nicht möchten, können Sie dieses Verhalten für einen Teil des Layouts oder das gesamte Layout natürlich überschreiben. Um dies zu steuern, können Sie Höhen-und Breiteneigenschaften verwenden.  
  
 Diese Seite beschreibt LayoutPanel-Elemente und Steuerelemente und leitet Sie dann weiter zu kurzen Videos, mit deren Hilfe sie einen Einstieg finden.  
  
> [!NOTE]
>  Einige Videos beziehen sich möglicherweise auf Blend oder Expression Blend, die den gleichen XAML-Designer wie Visual Studio und Blend für Visual Studio verwenden.  
  
## <a name="layout-panels"></a>Layoutbereiche  
 Starten Sie die Seite durch Auswahl eines dieser Layoutpanels. Ihre Seite kann mehrere Panele enthalten. Sie können z.B. mit einem Layoutbereich des Typs **Raster** beginnen und dann einem Bereich des **Rasters** ein **StackPanel** hinzufügen, um in diesem Element Steuerelemente vertikal anzuordnen.  
  
 Die folgenden LayoutPanel-Elemente sind die meisten allgemein verwendeten, aber es gibt noch andere. Sie befinden sich im Bereich **Bestand**.  
  
- [Raster](#Grid)  
  
- [UniformGrid](#Uniform)  
  
- [Canvas](#Canvas)  
  
- [StackPanel](#Stack)  
  
- [WrapPanel](#Wrap)  
  
- [DockPanel](#Dock)  
  
### <a name="Grid"></a> Raster  
 Anordnen von Objekten in Zeilen und Spalten.  
  
 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Verwendung von Rastern](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
### <a name="Uniform"></a> UniformGrid  
 Anordnen von Objekten in gleiche oder einheitliche Rasterbereiche. Dieser Bereich eignet sich hervorragend für die Anordnung einer Liste von Bildern.  
  
 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")  
  
 (Nur für WPF-Projekte verfügbar)  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [arbeiten mit einem UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
### <a name="Canvas"></a> Canvas  
 Anordnen von Objekten auf jede gewünschte Weise. Wenn Benutzer Ihre Anwendung ausführen, haben diese Elemente feste Positionen auf dem Bildschirm.  
  
 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [arbeiten mit dem Zeichnungsbereich](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
### <a name="Stack"></a> StackPanel  
 Horizontales oder vertikales Anordnen von Objekten in einer einzelnen Zeile.  
  
 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [arbeiten mit StackPanel und WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Wrap"></a> WrapPanel  
 Anordnen von Objekten nacheinander von links nach rechts. Wenn der Bereich am rechten Rand nicht genügend Platz aufweist, wird der Inhalt in die nächste Zeile *umgebrochen*, von links nach rechts und von oben nach unten. Sie können auch die ein WrapPanel-Element vertikal ausrichten, sodass Objekte von oben nach unten und von links nach rechts fließen.  
  
 (Nur für WPF-Projekte verfügbar)  
  
 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [arbeiten mit StackPanel und WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
### <a name="Dock"></a> DockPanel  
 Ordnet Elemente so an, dass sie an einer Kante des Panels bleiben (*andocken*).  
  
 (Nur für WPF-Projekte verfügbar)  
  
 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## <a name="layout-controls"></a>Layout-Steuerelemente  
 Sie können Ihre Objekte auch zu Layout-Steuerelementen hinzufügen. Sie sind haben keinen Funktionsumfang wie ein Layoutpanel, aber Sie werden für bestimmte Szenarien nützlich sein.  
  
 Die folgenden LayoutPanel-Elemente sind die meisten, allgemein verwendeten, aber es gibt noch andere. Sie finden Sie alle im Bereich **Bestand**.  
  
- [Randbereich](#Border)  
  
- [Popup](#Popup)  
  
- [ScrollViewer](#Scroll)  
  
- [UniformGrid](#Uniform)  
  
- [Viewbox](#View)  
  
### <a name="Border"></a> Rahmen  
 Erstellen Sie einen Rahmen, Hintergrund oder beides rund um ein Objekt. Sie können einem **Rahmen** nur ein Objekt hinzufügen. Wenn Sie einen Rahmen oder Hintergrund für mehrere Objekte benötigen, fügen Sie einen Layoutbereich zum **Rahmen** hinzu. Dann fügen Sie Objekte zu diesem Panel oder Steuerelement hinzu.  
  
 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")  
  
 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Funktionen](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [arbeiten mit Rahmen](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
### <a name="Popup"></a> Popup  
 Anzeigen von Informationen oder Optionen für Benutzer in einem Fenster. Sie können einem **Popup** nur ein Objekt hinzufügen. In der Standardeinstellung enthält ein **Popup** ein **Raster**. Dies lässt sich jedoch ändern.  
  
### <a name="Scroll"></a> ScrollViewer  
 Ermöglicht Benutzern, den Bildlauf auf einer Seite oder ein einem Bereich zu verwenden. Sie können einem **ScrollViewer** nur ein Objekt hinzufügen. Deshalb ist es sehr sinnvoll, einen Layoutbereich hinzuzufügen, z.B. ein **Raster** oder ein **StackPanel**.  
  
 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")  
  
### <a name="View"></a> Viewbox  
 Skalieren von Objekten ähnlich wie bei einem Zoomsteuerelement. Sie können einer **Viewbox** nur ein Objekt hinzufügen. Wenn Sie diesen Effekt auf mehr als ein Objekt anwenden möchten, fügen Sie der **ViewBox** einen Layoutbereich mit Steuerelementen hinzu.  
  
 (Nur für WPF-Projekte verfügbar)  
  
 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")  
  
## <a name="see-also"></a>Siehe auch  
 [Working with elements in XAML Designer](../designers/working-with-elements-in-xaml-designer.md)   
 [Erstellen einer Benutzeroberfläche mit dem XAML-Designer in Visual Studio](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
